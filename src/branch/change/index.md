---
layout: home
title: "브랜치 생성과 이동"
keyword: "브랜치 생성과 이동"
---

# 브랜치 생성과 이동
---
깃의 브랜치를 생성하는 동작과 이동하는 동작은 별개입니다. 브랜치 생성은 branch 명령어를 사용하고, 브랜치 이동은 checkout 명령어를 사용합니다. 브랜치를 생성하면서 동시에 생성된 브랜치로 이동하려면 별도의 명령을 실행해야 합니다.  

<br>
<a name="1"></a>

## 자동 이동 옵션
---
브랜치 생성과 이동 명령을 따로 두 번씩 입력하는 것은 불편합니다. 깃은 브랜치 생성과 이동 명령을 한 번에 처리하는 옵션을 제공합니다. 다음과 같이 체크아웃할 때 -b 옵션을 같이 사용하면 브랜치 생성과 이동을 한 번에 할 수 있습니다.  

```
$ git checkout -b 브랜치이름
```
 
브랜치 생성과 체크아웃을 동시에 하는 실습을 하겠습니다. -b 옵션으로 브랜치를 생성하면서 동시에 체크아웃도 합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git checkout -b hotfix ☜ 체크아웃합니다
Switched to a new branch 'hotfix' ☜ ①브랜치를 생성합니다

infoh@DESKTOP MINGW64 /e/gitstudy06 (hotfix) ☜ ②체크아웃
```

새로운 브랜치가 생성된 메시지와 함께 hotfix 브랜치로 자동 전환되었습니다. 브랜치 목록을 살펴봅시다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (hotfix)
$ git branch -v
  feature d84766c first
  footer  d84766c first
* hotfix  dcdb1c1 master working...
  master  dcdb1c1 master working...
```

새로운 hotfix 브랜치가 보이고 앞에 별표(*)가 표시된 것을 확인할 수 있습니다.  

<br>
<a name="2"></a>

## 커밋 이동
---
브랜치 이동을 좀 더 자세히 알아보겠습니다. 브랜치는 특정한 커밋에 별명을 부여한 것과 같습니다. 일반적으로 브랜치를 생성할 때는 마지막 커밋을 기준으로 합니다. 그리고 커밋 해시 값을 지정한 별칭으로 브랜치 목록에 등록합니다.  

이러한 동작 원리로 볼 때 브랜치 이름은 커밋 해시키와 동일합니다. 따라서 브랜치로 이동할 때 꼭 브랜치 이름만 사용할 필요는 없습니다. 브랜치 이름 대신 커밋 해시키를 사용하여 체크아웃할 수도 있습니다.  

```
$ git checkout 커밋해시키
```
 
커밋 해시키를 사용하여 체크아웃하려면 해시키를 알고 있어야 합니다. 커밋 해시 값은 40자리로 매우 길어 입력할 때 오류가 많이 생깁니다. 해시키를 전체 사용하지 않고, 앞의 7자리 정도만 사용해도 무리가 없습니다. 이는 유일한 해시 값이 가지는 특징입니다. 7자리만 사용해도 중복될 확률이 적습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (hotfix)
$ git branch -v
  feature d84766c first
  footer  d84766c first
* hotfix  dcdb1c1 master working...
  master  dcdb1c1 master working...
```

이번에는 브랜치 이름 대신에 직접 master 브랜치의 dcdb1c1 커밋 값을 사용하여 체크아웃해 볼까요?  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (hotfix)
$ git checkout dcdb1c1
Note: checking out 'dcdb1c1'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at dcdb1c1 master working...

infoh@DESKTOP MINGW64 /e/gitstudy06 ((dcdb1c1...))
```

지정한 커밋 위치로 체크아웃되었습니다. 깃 배시의 브랜치 이름에 입력한 커밋 해시 값이 표시됩니다. 이처럼 브랜치 중간에 작업한 특정 커밋으로 직접 이동하여 상태를 확인할 수 있습니다.  

<br>
<a name="3"></a>

## HEAD를 활용한 이동
---
커밋의 해시키를 사용하여 체크아웃하려면 복잡한 해시키를 알고 있어야 합니다. 또 복잡한 영어와 숫자로 표현하므로 입력 오류도 많이 생깁니다. 좀 더 간편하게 HEAD 포인터를 사용하여 체크아웃할 수도 있습니다. 예를 들어 바로 이전 커밋으로 체크아웃하고 싶을 때는 다음 명령을 실행합니다.  

```
$ git checkout HEAD~1
```

마지막 커밋인 HEAD를 기준으로 1단계의 커밋 상태로 이동합니다.  

그림 6-14] HEAD 기준 이동  
![HEAD 기준 이동](./img/06-14.jpg)


여러 단계 이전으로 이동하고자 한다면 뒤에 있는 숫자만 바꿉니다.  

```
$ git checkout HEAD~5
```

<br>
<a name="4"></a>

## 돌아오기
---
커밋 해시키 또는 HEAD를 사용하여 과거의 커밋으로 체크아웃했다면 다시 현재 시점으로 돌아와야 합니다. 간단하게 다시 돌아오는 방법은 대시(-)를 사용하는 것입니다.  


```
$ git checkout -
```

대시(`-`)를 사용하면 바로 이전의 브랜치로 복귀합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy06 ((dcdb1c1…))
$ git checkout -
Switched to branch 'hotfix'
infoh@DESKTOP MINGW64 /e/gitstudy06 (hotfix)
```

커밋 단계를 여러 번 이동한 후 원래 브랜치(현재)로 되돌아오려면 대시(-) 명령어를 여러 번 실행해야 합니다. 이때는 그냥 직접 브랜치 이름을 입력하는 것이 편리합니다.  

```
$ git checkout master
```

이 명령을 실행하면 master 브랜치로 이동합니다. 브랜치 이름을 입력하면 브랜치의 마지막 커밋 위치인 HEAD 포인트로 복귀합니다.  

<br><br>