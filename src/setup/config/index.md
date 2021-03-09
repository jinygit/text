---
layout: git
title: "깃 환경설정"
keyword: "git, 깃, 환경설정, 깃사용법, 깃허브, 소스트리, 깃교과서"
breadcrumb:
- "setup"
---

# 깃 환경설정
---


## 환경설정
깃은 모든 환경 정보를 .gitconfig 라는 환경 파일에 저장이 됩니다.

git의 명령어 config를 이용하면 직접 .gitconfig 파일을 수정하지 않고도 사용자 환경을 설정할 수 있습니다.
`git config` 의 명령들은 `--list` 옵션으로 확인할 수 있습니다.

```
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
:
... 추가생략
```

마지막 줄에 `:`가 표시가 되는데, 이는 더 보여줄 명령들이 있다는 것입니다.
엔터를 누르면 계속해서 추가 명령어들을 더 볼 수 있습니다.  
그만보고 밖으로 빠져나가 실려고 하면 `q`키를 누르시면 실행이 중단됩니다.

설정된 config의 파일을 수정하고자 한다면 `-e` 옵션을 사용합니다.

```
git config -e
```

이렇게 입력을 하게 되면 작업중인 깃 저장소의 `.git/config`을 수정하게 됩니다.

만일 전역 config 설정을 변경을 원한다면 `--global`옵션을 같이 사용합니다.

```
git config --global -e
```

`-e` 옵션으로 실행되는 편집기는 기본 설정된 `vi`에디터 입니다. vi 에디터를 사용하기 위해서는 관련 명령어들을 몇가지 알아 두셔야 합니다. 만일, 다른 편집기로 수정을 원하신다면 직접 경로를 입력하여 파일을 읽어 수정할 수 있습니다.

예를들어, vscode로 수정을 원하신다면 아래와 같이 입력을 합니다.
```
code .git/config
```


### 코드 편집기 수정해 보기

git의 기본 편집기를 vscode로 변경해 봅니다.

```
git config core.editor "code"
```

수정된 편집기가 정상적으로 실행이 되는지 실습을 해봅니다.

```
git config -e

infoh@hojin1 MINGW64 /d/jinydev/gittext (master)
$ 
```

환경설정을 위해서 vscode 창이 실행되고, 터미널은 다음 명령을 기다리게 됩니다.
이는 편집기인 vscode와 터미널 명령이 비동기적으로 각자 실행이 되는 것과 같습니다.

만일, git이 vscode로 수정된 결과를 기다린후에, 다음 명령을 수행할 수 있도록 할려고 한다면 `--wait` 값도 같이 입력을 합니다.

```
$ git config core.editor "code --wait"
$ git config -e
hint: Waiting for your editor to close the file... 
```

`--wait`값을 같이 설정하게 되면 깃은 `hint: Waiting for your editor to close the file... ` 메시지를 출력하고, vscode에서 파일 편집이 다 완료되어 저장되기를 기다리게 됩니다. 수정작업을 한후에 파일을 닫아 주세요. 그러면 다시 깃명령을 받을 수 있는 터미널 입력 상태가 됩니다.


### CRLF
윈도우와 리눅스/맥같은 운영체제는 파일의 줄바꿈 표시 방식이 약간 다릅니다. 이러한 차이점으로 몇가지 경고(waring)이 발생되는데,
이를 방지하기 위해서 crlf 설정을 추가해 줍니다.



#### 윈도우
윈도우는 파일의 줄바꿈시 `/r`과 `/n`이 동시에 들어가게 됩니다.

```
git config --global core.autocrlf true
```

autocrlf를 `true`로 설정을 하게 되면, 윈도우에서 깃으로 저장할때 `/r`을 제거하여 저장을 합니다.
반대로 깃에서 문서를 윈도우로 불러 올때는 `/r/n`으로 `/r`을 자동으로 추가하게 됩니다.

#### 리눅스/맥
리눅스/맥은 윈도우와 다르게 `/n` 한개만 사용합니다.

```
git config --global core.autocrlf input
```
autocrlf를 `input`으로 설정하게 되면,깃에서 읽어올때는 별도의 수정을 하지 않지만 저장을 할때에는 자동으로 `/n`만 붙여 주게 됩니다.
이는 실수로 `/r`이 추가되는 것을 방지하기 위해서 입니다.


