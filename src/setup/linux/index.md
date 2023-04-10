---
layout: home
title: "Git 교과서"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
breadcrumb:
- "setup"
- "linux"
---

# 리눅스용 깃
---
리눅스는 유닉스에서 파생된 운영체제 입니다. 또한, 리눅스는 전세계에서 가장 많은 서버로 운영되는 환경입니다. 클라우드, 서버용 환경을 같이 개발하는 경우에는 리눅스용 깃 환경이 필요할 것입니다.  

<br>

## 리눅스 설치
---
리눅스 운영체제는 독립된 컴퓨터 환경입니다. 실습을 위해서는 별도의 서버용 컴퓨터 환경이 필요합니다.  

하지만, 최근들어 마이크로소프트는 윈도우 사용자들도 리눅스를 사용해 볼 수 있도록 별도의 프로그램을 제공합니다.  

윈도우->스토어에서 ubuntu를 검색하여 설치를 할 수 있습니다. 우분투(ubuntu)는 데비안 계열의 리눅스 배포본 입니다.  

![](./img/linux01.png) 

윈도우에서 실행되는 리눅스 환경을 WSL(windows subsystem linux)라고 합니다. 이를 위해서는 별도의 설정이 필요합니다.  

파워셀을 실행하여 다음과 같이 명령을 입력 합니다.  

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

![](./img/linux02.png)  

Yes를 선택후 컴퓨터를 재부팅합니다.  

스토어에서 ubuntu를 선택하여 설치를 합니다. 설치가 완료된 후에 우분투 환경을 실행합니다. 우분투가 처음 실행이 될때에는 약간의 추가 설치 시간이 필요로 합니다.  

![](./img/linux03.png)  

윈도우에서 우분투 리눅스 환경이 구축되었습니다.  

<br>

## 깃 설치
---
리눅스 운영체제에서 깃을 설치하는 방법은 간단합니다. 직접 깃의 공식사이트에서 설치파일을 다운로드 받지 않아도 됩니다.  

대부분의 리눅스 배포판은 관련된 응용프로그램을 패키지 형태로 제공을 합니다.직접 소스코드를 다운로드 받아 복잡한 컴파일 작업을 하지 않아도 됩니다. 패키지는 리누스 배포본마다 약간의 차이가 발생합니다.  

깃을 설치하기 위해서는 먼저 자신의 리눅스 배포본과 환경을 알아야 합니다. 다음과 같이 입력하여 자신의 환경을 확인을 합니다.  

```
root@hojin1:~# cat /etc/issue
Ubuntu 18.04.2 LTS \n \l
```

리눅스 패키지를 다운로드 받아 설치를 합니다. 만일, 자신의 리눅스 배포판이 Fedora, CentOS 계열이라면 yum 명령어를 통하여 깃을 설치할 수 있습니다.  

```
$ sudo yum install git
```

데비안 계열의 우분투는 apt 명령을 사용합니다.  

```
$ sudo apt install git
```

최근들어 깃은 리눅스 시스템의 기본 설치 페키지 입니다. 대부분 리눅스 운영체제들은 깃을 기본적으로 탑제되어 있습니다. `–-version` 옵션으로 설치된 깃을 확인 할 수 있습니다.  

```
root@hojin1:~# git --version
git version 2.17.1
```
<br>

## 재설치
---
기존의 설치되어 있던 깃 패키지를 삭제하고 다시 설치를 해보도록 합니다. `remove` 옵션을 사용하여 설치되어 있는 `git`을 제거합니다.  

```
root@hojin1:~# apt remove git
Reading package lists... Done
Building dependency tree
Reading state information... Done
중간생략 …
Removing ubuntu-server (1.417.1) ...
Removing git (1:2.17.1-1ubuntu0.4) ...
```

이번에는 새롭게 깃을 설치해 보도록 합니다.  

```
root@hojin1:~# apt install git
Reading package lists... Done
Building dependency tree
Reading state information... Done
중간생략 …
Preparing to unpack .../git_1%3a2.17.1-1ubuntu0.4_amd64.deb ...
Unpacking git (1:2.17.1-1ubuntu0.4) ...
Setting up git (1:2.17.1-1ubuntu0.4) ...
```

정상적으로 설치가 잘 되었습니다.  

그 이외의 버전의 리눅스 배포판은 깃 공식사이트에 접속을 하여 설치 파일 또는 소스를 다운로드 받아 컴파일 하여 설치를 할 수 있습니다.  

<br>



## 최신버전 설치

---

깃 최신 패키지를 제공하는 저장소를 등록한 후, 깃을 재설치 합니다.

```
sudo add-apt-repository ppa:git-core/ppa -y
sudo apt-get update
sudo apt-get install git -y
git --version
```

