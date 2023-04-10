---
layout: home
title: "브랜치 이동"
keyword: "브랜치 이동"
breadcrumb:
- "branch"
- "checkout"
- "out"
---

# 체크아웃
---
호텔에서 퇴실할 때 체크아웃이라는 말을 합니다. 체크아웃은 객실을 비우고 떠나는 것을 의미합니다.  
즉, 현재 브랜치를 떠나 새로운 브랜치로 들어간다는 의미입니다.  

<br>

## 브랜치 이동
---
깃에서 브랜치 간 이동할 때는 checkout 명령어를 사용합니다.  

```
$ git checkout 브랜치이름
```

<br>

## 워킹디렉토리
---
checkout 명령어로 브랜치 간 이동하면서 실습해 보겠습니다.  
주의할 점은 깃은 하나의 워킹 디렉터리만 가지고 있다는 것입니다. 워킹 디렉터리는 선택한 브랜치 하나만 연결되어 있습니다.  
즉, 한 브랜치에서만 `작업`과 `커밋`을 할 수 있습니다.  

따라서 다른 브랜치에서 작업하려면 반드시 브랜치를 변경하여 워킹 디렉터리를 `재설정`해야 합니다.  

>Note: 워킹 디렉터리에 커밋하지 않은 내용이 있다면 브랜치를 변경할 수 없습니다.  

<br>

## 체크아웃 실습
---
checkout 명령어를 사용하여 footer 브랜치로 변경해 봅시다.  

```
infoh@DESKTOP-MINGW64 /e/gitstudy06 (feature)
$ git checkout footer
Switched to branch 'footer'
infoh@DESKTOP MINGW64 /e/gitstudy06 (footer)
```

현재 브랜치는 feature입니다.  

체크아웃하면 `Switched to branch ‘footer’` 메시지가 출력됩니다.  
footer 브랜치로 변경했다는 의미입니다.  
그리고 깃 배시에서도 변경된 브랜치 이름(footer)을 출력합니다.  

<br>

## 브랜치 이동처리
---
깃의 체크아웃은 거의 순간적으로 실행됩니다.  
깃은 빠르게 포인터를 이용하여 `빠르게 브랜치를 이동`할 수 있는 것이 `장점`입니다.  

다시 브랜치 `목록`을 확인합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (footer)
$ git branch -v
  feature d84766c first
* footer  d84766c first
  master  d84766c first
```

별표(`*`)가 footer 브랜치 이름 앞으로 변경된 것을 확인할 수 있습니다.  

<br>

## 커밋, 파일로 체크아웃
---
체크아웃은 브랜치 외에 특정 `커밋`이나 `파일`로도 할 수 있습니다.  

```
$ git checkout 브랜치 ☜ 브랜치로 체크아웃
$ git checkout -- 파일명 ☜ 파일로 체크아웃
```

> Note: 이중 대시(`--`)를 사용하면 파일 이름을 정확히 지정하여 브랜치를 변경할 수 있습니다.  
> 이렇게 하면 깃의 다른 옵션 명령어와 혼동하지 않습니다.  

<br>