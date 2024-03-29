---
layout: home
title: "HEAD 포인터"
keyword: "HEAD 포인터"
---

# HEAD 포인터
---
깃은 객체의 포인터 개념을 사용합니다. 대표적인 객체 포인터는 HEAD입니다. 깃 동작을 정확히 이해하려면 먼저 HEAD가 무엇인지 알아 두는 것이 좋습니다.   

<br>
<a name="1"></a>

## 마지막 커밋
---
깃은 마지막 커밋 정보가 중요합니다. 깃은 마지막 커밋 정보를 기반으로 새로운 커밋을 생성합니다. 마지막 커밋은 새로운 커밋의 부모 커밋입니다.  

시스템이 매번 커밋할 때마다 마지막 커밋 정보를 찾으면 부하가 발생합니다. 깃은 마지막 커밋을 쉽게 확인할 수 있도록 특수한 포인터를 제공합니다. HEAD는 작업 중인 브랜치의 마지막 커밋 ID를 가리키는 참조 포인터입니다.  

깃은 마지막 커밋을 가리키는 HEAD 포인터를 부모 커밋으로 대체하여 사용합니다. HEAD 포인터를 사용하여 빠르게 스냅샷을 생성할 수 있습니다.  

커밋 로그를 이용하여 HEAD를 확인해 보겠습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (footer)
$ git checkout footer ☜ 브랜치를 이동합니다
Switched to branch 'footer'

infoh@DESKTOP MINGW64 /e/gitstudy06 (footer)
$ git log --graph --all
* commit dcdb1c1fa4ef78bedd8dc13bc267e99391cc9782 (master)
| Author: hojin <infohojin@gmail.com>
| Date:   Sat May 11 18:45:35 2019 +0900
|     master working...
|
* commit d84766c7f87b1d9d234050949c48681ba4e35da8 (HEAD -> footer, feature) ☜ HEAD 위치
  Author: hojin <infohojin@gmail.com>
  Date:   Sat May 11 17:10:02 2019 +0900
      First

```

master 브랜치의 마지막 커밋은 dcdb1c1이고, footer 브랜치의 마지막 커밋은 d84766c입니다. master 브랜치에서 새로운 커밋을 생성할 때 부모 커밋으로 dcdb1c1을 가리키는 HEAD 포인터를 사용합니다. footer 브랜치에서 새로운 커밋을 생성할 때는 d84766c를 가리키는 HEAD 포인터를 사용합니다. 그리고 각 브랜치의 마지막 HEAD 포인터를 사용하여 커밋합니다. 현재 HEAD는 footer 브랜치의 d84766c를 가리킵니다.  

<br>
<a name="2"></a>

## 브랜치 HEAD
---
브랜치를 이동하면 HEAD 포인트도 이동됩니다. 브랜치가 여러 개면 HEAD 포인트도 여러 개입니다. 각각의 브랜치마다 마지막 커밋이 다르기 때문입니다. 브랜치마다 마지막 커밋 ID를 가리키는 HEAD 포인터가 하나씩 있습니다.  

그럼 브랜치 변경과 HEAD 포인터의 위치 변화를 실습으로 알아보겠습니다. master 브랜치로 이동하여 HEAD 위치를 확인해 봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (footer)
$ git checkout master ☜ 브랜치를 이동합니다
Switched to branch 'master'

infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git log --graph --all
* commit dcdb1c1fa4ef78bedd8dc13bc267e99391cc9782 (HEAD -> master) ☜ HEAD 위치
| Author: hojin <infohojin@gmail.com>
| Date:   Sat May 11 18:45:35 2019 +0900
|     master working...
|
* commit d84766c7f87b1d9d234050949c48681ba4e35da8 (footer, feature)
  Author: hojin <infohojin@gmail.com>
  Date:   Sat May 11 17:10:02 2019 +0900
      first
```

master 브랜치로 변경한 후 HEAD 포인터 위치는 이동된 브랜치의 마지막 커밋 dcdb1c1을 가리킵니다. HEAD 포인터는 브랜치에 따라서 위치가 달라집니다. HEAD는 현재 작업하는 브랜치를 가리키기 때문입니다.  

<br>
<a name="3"></a>

## 소스트리 HEAD
---
소스트리에서도 HEAD 포인트 상태를 쉽게 확인할 수 있습니다. 각 브랜치의 마지막 위치를 브랜치 아이콘으로 표시합니다. 예를 들어 각 브랜치마다 마지막 커밋을 HEAD 포인트로 표시합니다.  

그림 6-11] 소스트리에서의 HEAD  
![소스트리에서의 HEAD](./img/06-11.jpg)

HEAD 위치는 각 브랜치의 커밋 개수에 따라 서로 다르게 표시합니다.  

<br>
<a name="4"></a>

## 상대적 위치
---
깃의 HEAD 포인터는 내부적으로 커밋을 생성하고 브랜치를 관리하는 데 매우 유용합니다. 또 깃의 다양한 명령어를 입력할 때도 기준점으로 사용합니다. 마지막 커밋 위치인 HEAD를 기준으로 상대적 커밋 위치도 지정할 수 있습니다.  

상태적 커밋 위치를 지정할 때는 캐럿(^)과 물결(~) 기호를 같이 사용합니다. ^과 ~은 HEAD를 기준으로 몇 번째인지 상대적인 위치를 지정합니다. 예를 들어 HEAD 포인터 바로 이전의 커밋을 가리킨다면 HEAD^ 또는 HEAD~처럼 사용합니다.  

그렇다면 HEAD를 기준으로 이전 3개 위치를 지정하고 싶다면 어떻게 할까요? ^과 ~ 기호는 각각 하나의 상대적 위치를 의미하기 때문에 HEAD^^^, HEAD~~~처럼 사용합니다. 하지만 좀 더 먼 상대적 위치를 지정할 때는 기호가 많아져 이렇게 사용하기 어렵습니다. 이때는 숫자를 사용하여 HEAD^3 또는 HEAD~3처럼 표현합니다.  

>Note: 최근의 특정 위치를 지정할 때는 100644처럼 해시키를 사용하는 것이 편리합니다.  

<br>
<a name="5"></a>

## AHEAD, BHEAD
---
HEAD 앞에 A 또는 B가 붙은 AHEAD와 BHEAD 포인터도 있습니다. 원격 저장소와 연동하여 깃을 관리한다면 브랜치마다 HEAD가 2개 있습니다. 로컬 저장소 브랜치의 HEAD 포인터와 원격 저장소 브랜치의 HEAD 포인터입니다.  

원격 저장소와 로컬 저장소는 물리적으로 서로 다른 저장소입니다. 따라서 두 저장소의 마지막 커밋 위치가 일치하지 않을 수 있습니다. 이는 서로 다른 커밋을 가리키는 HEAD 포인터를 가진다는 의미입니다.  

AHEAD와 BHEAD는 서로 다른 저장소 간 HEAD 포인터의 위치 차이를 의미합니다. 깃은 항상 원격 저장소의 HEAD와 로컬 저장소의 HEAD를 비교합니다. HEAD는 브랜치마다 다릅니다. 브랜치를 여러 개 운영한다면 다수의 AHEAD와 BHEAD가 생길 수 있습니다.  

* AHEAD  
AHEAD는 서버로 전송되지 않은 로컬 커밋이 있는 것입니다. 예를 들어 로컬 저장소에 새로운 커밋을 생성하고, 새로운 커밋 정보를 서버로 전송하지 않는 상황입니다. 이런 경우 AHEAD가 발생합니다.  

그림 6-12] AHEAD  
![AHEAD](./img/06-12.jpg)

로컬 저장소의 HEAD 포인터를 기준으로 로컬 브랜치에 있는 커밋이 서버의 커밋 개수보다 많은 경우입니다.  

* BHEAD
BHEAD는 로컬 저장소로 내려받지 않은 커밋이 있는 것입니다. 예를 들어 누군가 서버에 새로운 커밋을 했습니다. 아직 로컬 저장소는 서버의 새로운 커밋을 내려받지 않았습니다. 이런 경우 BHEAD가 발생합니다.  

그림 6-13] BHEAD  
![BHEAD](./img/06-13.jpg)

다른 개발자가 코드를 수정하여 원격 저장소의 커밋이 자신의 로컬 저장소보다 더 최신 상태인 것을 의미합니다.  

<br><br>