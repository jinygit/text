# 객체
깃은 컨덴츠를 객체 형태로 저장을 합니다. 깃의 컨덴츠를 담고 있는 객체에 대해서 알아봅니다. 

## 객체폴더
객체들은 .git/objects 디렉토리에 저장이 됩니다. 저장소의 내용을 한번 살펴 봅니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/gitstudy19 (master)
$ ls .git/objects/
info/  pack/
```

objects 폴더안에는 두개의 서브 폴더가 존재합니다. 이 폴더는 깃 초기화(init)과 같은 작업시 자동으로 Info와 pack 를 생성합니다.

## hash-object
저수준 hash-object 명령은 입력된 컨덴츠의 SHA1 해쉬값을 출력합니다. 파일을 하나 생성합니다.

```
hello.md
Hello world!
```

Hash-object 명령을 통하여 hello.md 파일의 컨덴츠를 SHA1 값으로 확인해 봅니다. 

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git hash-object hello.md -w
6769dd60bdf536a83c9353272157893043e9f7d0
```

SHA1의 값은 40자리 입니다. -w 옵션을 같이 사용하면 해시를 객체로 같이 저장을 하게 됩니다. 

저장된 객체를 확인해 봅니다. 리눅스 find 명령어를 이용하여 객체 폴더안에 파일만 검사를 해봅니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ find .git/objects/ -type f
.git/objects/67/69dd60bdf536a83c9353272157893043e9f7d0
```

앞에서 생성된 SHA1 해쉬값 으로 객체파일 하나가 생성된 것을 확인할 수 있습니다. SHA1 해쉬값의 2자리는 디렉토리로 사용을 합니다. 나머지 값은 파일명으로 사용을 합니다.

즉, 깃은 컨덴츠를 이용하여 해쉬값을 생성하고, 해쉬값을 이용하여 파일을 생성합니다.

## cat-file
이번에는 hash-object로 생성된 객체의 내용을 확인해 봅니다. 셀 명령어 cat은 파일의 내용을 출력합니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ cat .git/objects/67/69dd60bdf536a83c9353272157893043e9f7d0
xK▒▒OR04b▒H▒▒▒W(▒/▒IQB▒▒
```

하지만 생성된 깃의 객체는 일반적인 cat 명령으로 확인을 할 수 없습니다. 이를 위해서 깃은 별도의 저수준 명령어 cat-file을 제공합니다.

깃 cat-file 명령을 사용하여 앞에서 생성된 객체의 내용을 다시 한번 확인해 보도록 하겠습니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git cat-file -p 6769dd60bdf536a83c9353272157893043e9f7d0
Hello world!
```

우리가 알아볼 수 형태의 텍스트로 출력이 되었습니다. 앞에서 생성한 hello.md 파일의 내용과 동일한 것을 확인할 수 있습니다.

*	-p 옵션: 컨덴츠 내용을 출력합니다.
*	-t 옵션: 타입을 출력합니다.

옵션과 해시값을 입력하면 됩니다.

## Blob
깃은 Content addressable 기반으로 입력된, 파일의 내용을 기반으로 해시 주소를 생성합니다. 만일 파일의 내용(컨덴츠)이 달라지면 해쉬값도 변경이 됩니다. 그리고 해쉬값을 파일명으로 사용을 합니다.

파일의 내용을 수정해 봅니다.

hello.md
```
Hello world!
만나서 반갑습니다.
```

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git hash-object hello.md -w
2dedc914313613dba23eefd923674adee9fe559c
```

해쉬값이 기존과 달라진 것을 확인할 수 있습니다. 내용이 변경이 되면 새로운 객체가 추가로 생성이 됩니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ find .git/objects/ -type f
.git/objects/2d/edc914313613dba23eefd923674adee9fe559c
.git/objects/67/69dd60bdf536a83c9353272157893043e9f7d0
```

현재 객체가 2개로 증가된 것을 확인할 수 있습니다. 새로운 객체의 내용을 확인해 보면 수정된 파일의 내용과 동일한 것을 보실 수 있습니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git cat-file -p 2dedc914313613dba23eefd923674adee9fe559c
Hello world!
만나서 반갑습니다.
```

이처럼 깃은 컨덴츠의 변경마다 객체를 생성하고 이를 구분하기 위해서 해시값을 파일명으로 사용합니다. 이러한 방식의 파일은 이력 관리를 위해서 장점이긴 하나 단점으로는 파일명을 알기 어렵다는 것입니다.

깃은 이러한 객체를 blob 이라고 표현을 합니다. cat-file -t 옵션을 이용하여 객체 파일이 어떠한 타입인지를 알려 줍니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git cat-file -t 6769dd60bdf536a83c9353272157893043e9f7d0
blob
```
