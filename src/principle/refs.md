---
layout: home
title: "Git 교과서"

keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---
# Refs
SHA1 해시를 직접 작업에 사용하기에는 가독성이 좋지 않습니다. 깃은 sha1 해시를 좀더 쉽게 사용할 수 있도록 refs 를 지원합니다.

## 포인터
지금까지 우리는 파일의 객체저장 과 트리, 커밋을 해보았습니다. 이렇게 작업한 결과를 log 명령을 통하여 확인해 보았습니다.

```
$ git log --stat 0ee97a
```

하지만 로그를 확인하기 위해서는 마지막 커밋의 `sha1` 해쉬값을 가지고 있어야 합니다.  
매번 커밋마다 복잡한 sha1 해쉬를 기억하여 사용하기에는 힘이 듭니다.

깃은 이러한 커밋 해시를 쉽게 접근할 수 있도록 `refs` 라는 포인터를 제공합니다.

## Refs 폴더
다음은 저장소의 Refs 내용입니다. 모든 커밋의 포인터는 `.git/refs` 폴더에 저장이 됩니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/gitstudy19 (master)
$ find .git/refs/
.git/refs/
.git/refs/heads
.git/refs/tags
```

아직 마스터(master) `refs`는 없습니다.  
새로운 `refs/master`를 추가해 봅니다. 마지막 커밋 해쉬를 `refs`에 추가해 봅니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ echo "0ee97afec0380e074080129b339e5d284f4ba7d9" > .git/refs/master
```

생성된 `refs/master`를 이용하여 로그 기록을 확인해 보도록 합니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git log --pretty=oneline master
0ee97afec0380e074080129b339e5d284f4ba7d9 (refs/master) second commit
9d2258ca2884b8a3813692ea2900a728f1276e0e first commit
```

이제 쉽게 로그 기록을 확인할 수 있게 되었습니다.  
하지만 아쉽게도 매번 커밋을 할때마다 `refs/master`를 새롭게 갱신해 주어야 합니다.

## update-ref
매 커밋마다 `ref/master`의 파일을 직접 수정을 하는 것은 바람직 하지 않습니다.  
깃은 `refs` 파일을 대신 수정할 수 있는 `update-ref` 명령을 제공합니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git update-ref refs/head/master 0ee97afec0380e074080129b339e5d284f4ba7d9
```

update-ref 명령을 통하여 refs 값을 갱신할 수 있습니다. 

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ cat .git/refs/head/master
0ee97afec0380e074080129b339e5d284f4ba7d9
```

체크아웃을 통하여 브랜치를 이동할 때, 브랜치는 항상 마지맛의 커밋의 HEAD를 가리키게 되어 있습니다.  
이 또한 Refs로 체크아웃은 매번 `update-ref` 를 통하여 HEAD 포인터를 갱신하는 것입니다.

