---
layout: home
title: "Git 교과서"

keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---
# 커밋
커밋은 작성자와 메시지 정보를 기록합니다. 하지만 깃의 Blob과 tree는 파일 구조과 컨덴츠의 객체만 보관만 합니다.

## 커밋 객체
우리가 일반적인 커밋 작성시 기록되는 정보들은 별도 객체에 저장을 해야 합니다. 이를 커밋 객체라고 합니다.  
깃은 실제 파일의 컨덴츠와 커밋의 정보를 구별합니다.

## commit-tree
커밋 객체는 커밋의 정보와 트리 객체를 이용하여 하나의 sha1 해쉬 객체로 저장을 합니다.  
저수준 명령어 `commit-tree`를 이용하여 새로운 커밋을 해보도록 합니다. 이는 고수준 명령인 `commit`과 같습니다.

커밋을 입력합니다. 첫번째 생성한 트리객체(1d784f1)로 합니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ echo "first commit" | git commit-tree 1d784f1
9d2258ca2884b8a3813692ea2900a728f1276e0e
```

커밋 메시지를 쉘 echo 명령과 파이프 명령을 통하여 `commit-tree`에 전달합니다.  
새로운 커밋이 하나 생성되었습니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git cat-file -p 9d2258c
tree 1d784f1a9e90692ba49d941f06fb955df7b28599
author hojin <infohojin@gmail.com> 1550479782 +0900
committer hojin <infohojin@gmail.com> 1550479782 +0900

first commit
```

두번째 커밋을 해보도록 합니다. 두번째 커밋은 객체트리(7308279)로 합니다.  
커밋은 링크 형태로 이전의 커밋을 참조하게 됩니다. `-p` 옵션을 이용하여 이전의 커밋 정보도 같이 넣어 줍니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ echo "second commit" | git commit-tree 7308279 -p 9d2258c
0ee97afec0380e074080129b339e5d284f4ba7d9
```

두번째 커밋을 생성하였습니다. 이렇게 생성된 두개의 커밋을 log 히스토리로 확인을 해보도록 합니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git log --stat 0ee97a
commit 0ee97afec0380e074080129b339e5d284f4ba7d9
Author: hojin <infohojin@gmail.com>
Date:   Mon Feb 18 18:04:44 2019 +0900
    second commit

 readme.md | 1 +
 1 file changed, 1 insertion(+)

commit 9d2258ca2884b8a3813692ea2900a728f1276e0e
Author: hojin <infohojin@gmail.com>
Date:   Mon Feb 18 17:49:42 2019 +0900
    first commit

 hello.md | 2 ++
 1 file changed, 2 insertions(+)
```

연결된 두개의 커밋 과 로그 기록을 확인해 볼 수 있습니다.  
이처럼 고수준의 `add` 명령과 `commit`을 사용하지 않고도 객체, 트리, 커밋을 할 수 있습니다.

지금까지 생성된 객체를 확인해 봅니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ find .git/objects -type f
.git/objects/0e/e97afec0380e074080129b339e5d284f4ba7d9
.git/objects/1d/784f1a9e90692ba49d941f06fb955df7b28599
.git/objects/2d/edc914313613dba23eefd923674adee9fe559c
.git/objects/67/69dd60bdf536a83c9353272157893043e9f7d0
.git/objects/73/08279e324e57a08b54670b6e2ee1e2b1ab2ac3
.git/objects/78/f58b67989cc07cd244e17909150b311fd5d35f
.git/objects/9d/2258ca2884b8a3813692ea2900a728f1276e0e
```

객체 폴더에는 `Blob`, `Tree`, `commit`등의 다양한 객체들이 sha1 해쉬에 따라 저장되는 구조를 확인 할 수 있습니다.

