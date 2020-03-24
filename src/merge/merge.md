---
layout: home
title: "Git 교과서"

keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---
# 병합
두개의 브랜치 작업을 하나의 브랜치로 커밋을 합치는 작업을 수행합니다.

## 병합 취소
두개의 브랜치를 병합시 수많은 출돌로 직전 병합 명령을 취소하고 싶은 경우가 있습니다.
`--abort` 명령은 직전의 병합 명령을 취소합니다.

```
충돌상태...
infoh@hojin1 MINGW64 /d/jiny2_2020/dbadmin (master|MERGING)       
$ git merge --abort

infoh@hojin1 MINGW64 /d/jiny2_2020/dbadmin (master)
```

## 병합 덥어쓰기
병합은 기본적으로 두개의 브랜치의 차이점을 비교하여 하나의 파일로 합치는 과정을 걸치게 됩니다.
하지만, 충돌사항이 많은 경우 강제로 하나의 브랜치로 덥어쓰기를 원하는 경우가 있습니다.
이 때 `-X theirs` 옵션을 사용합니다.

```
git merge -X theirs 브랜치
```

