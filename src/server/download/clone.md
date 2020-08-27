---
layout: git
title: "Git 서버에서 코드 내려받기"

breadcrumb:
- "server"
- "downlaod"
- "clone"
---

# 저장소 복제하기(clone)
---
`복제`는 기존 저장소를 이용하여 새로운 저장소를 생성하는 방법 중 하나입니다.  
하지만 일반적인 복제와 원격 저장소를 복제하는 방법은 조금 차이가 있습니다. 몇 가지 추가 정보를 같이 설정해야 합니다.  

<br>

## clone 명령
---
저장소를 복제할 때는 `clone` 명령어를 사용합니다.  
clone 명령어는 초기화 `init` 명령어 외에 원격 서버 접속에 필요한 추가 `설정을 자동으로 수행`합니다.  
서버의 연결 설정을 마친 후 서버 안에 있는 `모든 커밋된 코드 이력`들을 한 번에 내려받습니다.  

원격 저장소와 로컬 저장소 연결  
![원격 저장소와 로컬 저장소 연결](../img/05-9.jpg)

<br>

### clone 명령 실습
---
원격 저장소를 다른 이름의 로컬 저장소로 `복제`해 보겠습니다.  

<br>

#### 실습 폴더 생성
실습을 위해서 새로운 폴더를 생성합니다.
```
$ cd 메인폴더
$ mkdir gitstudy05_clone
$ cd gitstudy05_clone/
```

<br>

#### clone 명령 실행
원격저장소를 복제하기 위해서 clone 명령을 입력합니다.
```
infoh@hojin MINGW64 /e/gitstudy05_clone
$ git clone https://github.com/jinygit/gitstudy05.git .
Cloning into '.'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
```
정상적으로 잘 복제가 된것 같습니다.

<br>

#### 복제된 저장소 확인
원격 저장소가 로컬 저장소로 잘 복제가 되었는지 내용을 확인해 봅니다.

```
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ ls -all
total 13
drwxr-xr-x 1 infoh 197609  0 12월 12 17:23 .
drwxr-xr-x 1 infoh 197609  0 12월 12 17:23 ..
drwxr-xr-x 1 infoh 197609  0 12월 12 17:23 .git
-rw-r--r-- 1 infoh 197609 14 12월 12 17:23 README.md
```

원격저장소와 동일하 내용으로 복제가 된것을 확인할 수 있습니다.

<br>

## 서버접속 설정
---
원격 저장소를 활용하여 저장소를 동기화 하기 위해서는, 로컬저장소와 원격저장소간의 연결 정보를 설정해 주어야 합니다.  
하지만, 복제를 하게 되면 이러한 정보설정이 자동으로 이루어 집니다.

<br>

### 자동설정
---
복제란? 서버의 저장소를 로컬로 복사를 하는 동작입니다. 즉, 서버에 접속을 해야 되기 때문에 서버 정보가 필요로 합니다.  
clone 명령어 뒤에 서버의 url을 입력하게 되면, 깃은 원격 저장소를 복제한 후에 정보를 로컬에 자동 설정을 하게 됩니다.  

<br>

### remote 확인 
---
복제 후 자동으로 설정된 서버 연결 정보를 확인해 보도록 합니다.
`remote` 명령어를 사용하여 원격 저장소 정보를 확인합니다.  

```
infoh@gitstudy MINGW64 /e/gitstudy05_clone (master)
$ git remote -v
origin  https://github.com/jinygit/gitstudy05.git (fetch)
origin  https://github.com/jinygit/gitstudy05.git (push)
```

`remote`로 확인하면 연결된 서버 설정들이 표시됩니다.  

로컬 저장소를 생성한 후, 처음으로 서버에서 코드를 내려받을 때는 clone 명령어를 사용하면 좀 더 편리합니다.  

<br>