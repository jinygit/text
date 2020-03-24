---
layout: home
title: "Git 교과서"

keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---
# packfile
깃은 저장소를 효율적으로 사용하기 위해서 압축을 사용합니다.

## loose 포멧
커밋의 생성은 이전 커밋을 분석하여 차이점을 스넵삿을 저장을 합니다.  
이러한 스넵삿 저장방식은 기존의 파일단위 저장보다 적은 용량으로 테이터를 보관할 수 있는 장점이 있습니다.

사실 깃은 기본적인 객체의 생성시 모든 내용을 저장합니다. 이를 `loose` 포맷이라고 합니다. 

## 압축
저장소의 크기가 크면 `clone` 시 많은 시간과 용량을 차지하게 됩니다. 깃은 `zlib`을 사용하여 내용을 압축합니다.  
깃은 생성된 객체를 압출할 수 있는 저수준 명령어 `gc`를 제공합니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git gc
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (7/7), done.
Total 7 (delta 0), reused 0 (delta 0)
```

깃의 `gc` 명령은 객체를 압축합니다.  
깃은 압축과정에서 크기와 이름이 비슷한 파일들을 찾습니다. 이를 비교하여 다른 부분만을 별도로 저장합니다. 압축된 객체는 `objects/pack`에 저장이 됩니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ ls .git/objects/pack/
pack-a193464be55f93fb9b1b0e1edc55d18533e1ae64.idx
pack-a193464be55f93fb9b1b0e1edc55d18533e1ae64.pack
```

## 압축검증
압축한 내용을 `verify-pack` 명령을 이용하여 확인 할 수 있습니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git verify-pack -v .git/objects/pack/pack-a193464be55f93fb9b1b0e1edc55d18533e1ae64.pack
0ee97afec0380e074080129b339e5d284f4ba7d9 commit 216 145 12
3b9fa13c10c7744fdf611a77a2ac4db792c0baac tag    130 120 157
9d2258ca2884b8a3813692ea2900a728f1276e0e commit 167 116 277
7308279e324e57a08b54670b6e2ee1e2b1ab2ac3 tree   73 79 393
1d784f1a9e90692ba49d941f06fb955df7b28599 tree   36 47 472
2dedc914313613dba23eefd923674adee9fe559c blob   39 52 519
78f58b67989cc07cd244e17909150b311fd5d35f blob   29 42 571
non delta: 7 objects
.git/objects/pack/pack-a193464be55f93fb9b1b0e1edc55d18533e1ae64.pack: ok
```

## 자동 압축
깃은 공간을 절약하기 위해서 중간 중간 `gc` 명령을 자동 수행하여 압축을 실행합니다.

`pre-auto-gc` 훅스크립트는 자동 실행되는 `gc`를 감지할 수 있습니다.  
이를 통하여 자동실행되는 `gc`를 취소할 수도 있습니다.
