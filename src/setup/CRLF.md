---
layout: home
title: "Git 교과서"
description: "버전 관리 시스템의 이해와 설치부터 커밋, 브랜치, 임시 처리, 병합, 복귀, 서브모듈, 태그까지
깃, 소스트리, 깃허브로 실습하며 기본기를 탄탄하게 다진다!"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---
# CRLF
파일은 종료를 의미하는 `line ending`을 가지고 있습니다.

line ending은 운영체제 마다 다릅니다.
window 운영체제는 CR(\r) 과 LF(\n) 두개를 같이 사용합니다.

반면에 맥, 리눅스와 같은 운영체제는 LF(\n)만 사용을 합니다.

## line ending 설정
윈도우에서 git을 사용할때 이러한 line ending의 설정을 바꿀수 있습니다.


### core.eol
현재 시스템의 기본 line ending으로 처리를 합니다.
windows 시스템을 사용하는 경우 CRLF로 적용되며, 리눅스의 경우 LF로 설정됩니다.
```
git config --global core.eol native
```






