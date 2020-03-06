# Tree
깃의 객체는 우리가 처음에 생성한 원본의 파일이름으로 객체를 생성하지 않습니다. 복잡한 해쉬값을 이용하여 파일명을 대체하기 때문에 쉽게 파일을 구분할 수 없습니다.

## 트리객체
그럼 우리가 작성한 파일이름은 어디에 보관이 될까요? 

깃은 생성된 파일 이름을 tree 라는 객체에 별도로 저장을 합니다. 깃은 tree 와 blob 객체로 구분을 합니다. Tree는 디렉터리를 의미하고, blob은 파일을 의미합니다.

Tree 객체는 한 개의 파일 또는 여러 개의 파일을 저장할 수 있습니다.

## 트리 생성
새로운 트리 객체를 생성해 봅니다. 깃의 트리는 스테이지영역 상태를 기반으로 트리를 생성을 합니다. 따라서 생성한 파일을 스테이영역에 등록을 해주어야 합니다.

이전에는 간단하게 add 명령을 통하여 파일을 스테이징 하였다면, 이번에는 저수준 명령어 update-index를 사용해 보겠습니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git update-index --add --cacheinfo 100644 2dedc914313613dba23eefd923674adee9fe559c hello.md
```

생성된 파일을 스테이지영역에 처음으로 등록할 경우에는 --add 옵션을 같이 사용합니다. 또한, 깃 데이터베이스에 파일을 등록하기 때문에 --cacheinfo 옵션을 같이 사용합니다.

몇가지 옵션을 추가합니다. 파일모드, 해쉬값, 파일명을 같이 입력합니다.

파일모드
*	일반파일 : 100644
*	실행파일 : 100755
*	심볼파일 : 120000

리눅스에는 여러 파일모드가 있습니다. 깃의 blob은 위의 3가지 형태의 파일모드만 지원을 합니다.

스테이지에 파일을 등록하였습니다. 스테이지 영역을 기준으로 새로운 트리 객체를 생성해 봅니다. 

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git write-tree
1d784f1a9e90692ba49d941f06fb955df7b28599
```

저수준 명령어 write-tree는 스테이지 영역의 내용을 기준으로 새로운 트리 객체를 생성합니다. 새로운 트리 객체가 하나 더 생성된 것을 확인 할 수 있습니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git cat-file -t 1d784f1a9e90692ba49d941f06fb955df7b28599
tree
```

트리객체의 내용도 확인을 해봅니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git cat-file -p 1d784f1a9e90692ba49d941f06fb955df7b28599
100644 blob 2dedc914313613dba23eefd923674adee9fe559c    hello.md
```

이번에는 새로운 파일 하나를 더 생성하여 추가해 봅니다.

readme.md
```
# 깃 내부 학습입니다.
```

스테이지에 추가한 파일을 등록합니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git update-index --add readme.md
```

스테이지를 기반으로 새로운 트리 객체를 생성해 봅니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git write-tree
7308279e324e57a08b54670b6e2ee1e2b1ab2ac3
```

새로운 파일의 추가와 트리 객체는 별개로 구분을 합니다. 새롭게 생성된 트리 객체의 내용을 확인해 봅니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git cat-file -p 7308279e324e57a08b54670b6e2ee1e2b1ab2ac3
100644 blob 2dedc914313613dba23eefd923674adee9fe559c    hello.md
100644 blob 78f58b67989cc07cd244e17909150b311fd5d35f    readme.md
```
두개의 파일명과 blob 객체가 연결된 것을 보실 수 있습니다.

