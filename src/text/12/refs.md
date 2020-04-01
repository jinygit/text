---
layout: home
title: "refs"
keyword: "refs"
---

# refs
---
깃은 커밋으로 코드 이력을 관리합니다. 커밋은 고유의 SHA1 해시 값을 가지고 있으며, 이 해시
값은 여러 기능에서 참조합니다. 깃에서는 참조하는 해시 값을 refs 목록으로 가지고 있습니다.  

<br>
<a name="1"></a>

## 실습 환경 준비
---
먼저 refs 기능을 학습할 수 있도록 실습 환경을 만들겠습니다. 저장소를 생성합니다.  

```
$ cd 실습폴더
$ mkdir gitstudy12 새 폴더 만들기
$ cd gitstudy12
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git init 깃 초기화
Initialized empty Git repository in E:/gitstudy12/.git/
index.htm 파일을 생성합니다.
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ code index.htm VS Code 실행
index.htm
hello world
```

간단한 인사말만 작성했습니다. 저장한 후 커밋합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git add index.htm 등록
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git commit -m "first" 커밋
[master (root-commit) d0943cf] first
1 file changed, 1 insertion(+)
create mode 100644 index.htm
```

<br>
<a name="1"></a>

## 해시
---
깃에서 해시 값은 매우 중요합니다. 깃은 SHA1 알고리즘을 사용하여 해시 값을 생성합니다. 해
시 값은 깃의 동작을 구분하며, 중복되지 않는 유일한 값입니다.  

깃의 모든 작업은 SHA1 해시 값을 참조합니다. 깃 내부적으로 동작하는 작업들은 SHA1 해시 값
으로 연결 고리를 생성합니다. 따라서 깃의 동작을 정확히 이해하려면 해시 값을 자세히 알아볼
필요가 있습니다.  

생성된 모든 해시 값은 show 명령어로 확인할 수 있습니다.  

```
$ git show 해시값
```

저장소의 로그를 확인해 보겠습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git log 커밋 로그
commit d0943cfbc5e092668be3b96e98f32e363e05feb1 (HEAD -> master)
Author: hojin <infohojin@gmail.com>
Date: Sat May 25 18:06:47 2019 +0900
first
커밋 로그가 1개 출력됩니다. 출력된 d0943cf 해시 값의 정보를 확인해 봅시다.
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git show d0943cf 커밋 정보
commit d0943cfbc5e092668be3b96e98f32e363e05feb1 (HEAD -> master)
Author: hojin <infohojin@gmail.com>
Date: Sat May 25 18:06:47 2019 +0900
first
diff --git a/index.htm b/index.htm
new file mode 100644
index 0000000..95d09f2
--- /dev/null
+++ b/index.htm
@@ -0,0 +1 @@
+hello world
\ No newline at end of file
```

<br>
<a name="1"></a>

## 역조회
---
show 명령어는 해시 값을 사용하여 커밋 정보를 확인합니다. 반대로 rev-parse 명령어로 포인터
의 해시 값을 알 수 있습니다. 예를 들어 브랜치는 커밋 해시 값을 가리키는 포인터입니다. 따라서
브랜치 이름을 사용하여 참조하는 해시 값을 조회할 수 있습니다. master 브랜치의 해시 값을 확
인해 봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git rev-parse master
d0943cfbc5e092668be3b96e98f32e363e05feb1
```

<br>
<a name="1"></a>

## 참조 목록
---
깃은 SHA1 해시 값을 생성하고, 커밋은 생성된 해시 값을 간접적으로 사용합니다. 또 깃에서는
생성된 해시 값을 쉽게 참조할 수 있도록 refs 목록을 생성합니다. 깃의 모든 refs 목록은 저장소의
숨긴 영역인 .git/refs 폴더 안에 저장됩니다.  
또 복잡한 SHA1 해시 값을 쉽게 찾아 사용할 수 있도록 별칭도 쓸 수 있습니다. 별칭은 .git/refs
폴더 안에서 생성 및 관리할 수 있습니다. 즉, refs 정보는 깃의 기능들을 구현하는 내부 메커니즘
입니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ ls .git/refs -all 저장소 refs 파일 목록
total 4
drwxr-xr-x 1 infoh 197609 0 5월 25 18:02 .
drwxr-xr-x 1 infoh 197609 0 5월 25 18:06 ..
drwxr-xr-x 1 infoh 197609 0 5월 25 18:06 heads
drwxr-xr-x 1 infoh 197609 0 5월 25 18:02 tags
```

처음 저장소를 생성하면 .git/refs 폴더에는 heads와 tags 폴더만 있습니다. 새로운 브랜치를 만
들 때마다 해시 값을 가지는 refs 파일들을 생성합니다.  

새로운 feature 브랜치를 만들고 .git/refs 폴더를 확인합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git branch feature 브랜치 생성
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ ls .git/refs/heads -all 저장소 refs 정보
total 2
drwxr-xr-x 1 infoh 197609 0 5월 25 18:14 .
drwxr-xr-x 1 infoh 197609 0 5월 25 18:02 ..
-rw-r--r-- 1 infoh 197609 41 5월 25 18:14 feature 브랜치의 HEAD 포인트
-rw-r--r-- 1 infoh 197609 41 5월 25 18:06 master
```

feature 브랜치의 refs가 생성되었습니다.

<br><br>