---
layout: git
title: "Git 서버에서 코드 내려받기"
keyword: "git, unrelated pull"
description: "서로다른 저장소의 코드를 pull로 내려받는 방법에 대해서 알아 봅니다. "
breadcrumb:
- "server"
- "downlaod"
- "pull"
---

# Unrelated Histories Pull
---
pull을 통하여 원격 저장소의 커밋을 내려받기 위해서는 연속된 기록된 커밋 정보를 가지고 있는 저장소이어야 합니다.  
만일 연관성이 없는 별개의 원격 저장소는 pull로 내려 받을 수 없습니다.  

만일 이러한 동작이 필요하다면, 특수한 작업을 몇가지 해주어야 합니다.  

<br>

## 별개의 저장소 pull 하기
---
기존에 존재하는 `로컬저장소`에 새로운 원격 저장소를 등록하여 서버의 코드를 내려 받습니다. 

실습1 : 먼저 로컬저장소를 생성합니다.
```console
infoh@hojin1 MINGW64 /e/git/test/pull
$ git init .
Initialized empty Git repository in E:/git/test/pull/.git/
```

실습2 : 파일을 생성하고, 커밋을 합니다.
```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ echo "hello" > hello.md

infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git add .
warning: LF will be replaced by CRLF in hello.md.
The file will have its original line endings in your working directory

infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git commit -m "hello"
[master (root-commit) f5f72fd] hello
 1 file changed, 1 insertion(+)
 create mode 100644 hello.md
```

실습3: 새로운 원격저장소를 등록합니다.
```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git remote add origin https://github.com/hojinio/daelim_20202-2.git

infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git remote -v
origin  https://github.com/hojinio/daelim_20202-2.git (fetch)
origin  https://github.com/hojinio/daelim_20202-2.git (push)
```

실습4: 원격저장소에서 pull을 합니다.
```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git pull
warning: no common commits
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), 456 bytes | 38.00 KiB/s, done.
From https://github.com/hojinio/daelim_20202-2
 * [new branch]      master     -> origin/master
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> master
```

하지만, `pull` 동작을 하지 못하고 `오류`가 발생합니다.  
오류의 내용은 로컬저장소가 원격저장소의 트래킹 정보가 설정되어 있지 않기 때문입니다.

<br>

## 문제해결1
---
브랜치의 `업스트림` 설정을 해주어야 합니다.

```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git branch --set-upstream-to=origin/master master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

트래킹 설정으로 `로컬저장소의 master` 브랜치와 `원격저장소의 master` 브랜치를 연결하였습니다.
다시한번 `pull`을 시도해 봅니다.

```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git pull
fatal: refusing to merge unrelated histories
```

커밋 병합이 거절이 되었다고 메시지를 출력합니다.  
`pull` 동작은 `fetch`와 `merge`를 동시에 수행하는 동작입니다.  
메시지를 확인해 보면 이미 원격 저장소의 코드를 `fetch`한 상태 입니다.

```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git branch -vv
* master f5f72fd [origin/master: ahead 1, behind 2] hello
```

사실, 개별로 생성한 로컬저장소와 원격저장소는 서로 연관성이 없습니다.  
깃은 커밋을 생성할때 이전 커밋의 스냅샷을 이용하여 새로운 커밋을 생성합니다. 따라서 두개의 커밋의 상위 공통된 커밋이 존재하지 않기 때문에 병합을 할 수 없습니다.

`fetch`한 원격저장소의 내용으로 checkout 하여 내용을 살펴볼 수 있습니다. 하지만, 병합을 할 수는 없습니다.

```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git checkout origin/master
Note: switching to 'origin/master'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 07bd439 hello 123456-4

infoh@hojin1 MINGW64 /e/git/test/pull ((07bd439...))
$ ls
123456  123456-4

infoh@hojin1 MINGW64 /e/git/test/pull ((07bd439...))
```

다시 로컬저장소의 master로 체크아웃 합니다.

```
infoh@hojin1 MINGW64 /e/git/test/pull ((07bd439...))
$ git checkout master

```

좀더 구체적으로 이 현상을 알아 봅니다.  
로컬 저장소는 마지막의 커밋 정보를 HEAD에 담겨집니다.  
또한, fetch를 하게 되면 FETCH_HEAD에 원격저장소의 마지막 커밋 정보들 담게 됩니다.

이는 
```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git checkout FETCH_HEAD

infoh@hojin1 MINGW64 /e/git/test/pull ((07bd439...))
$ ls
123456  123456-4
```
와 동일합니다.

다시 master 브랜치로 돌아 옵니다.

```
infoh@hojin1 MINGW64 /e/git/test/pull ((07bd439...))
$ git checkout -
```

<br>

## 문제해결2
---
이러한 문제가 없도록 하는 방법은 처음부터 저장소를 생성한 후에 새로운 원격저장소를 만들어 유지하는 것입니다.  
또는, 기존의 원격저장소를 clone 하여 작업을 하는 것입니다.

이 문제를 해결하기 위해서는 강제로 `pull` 명령에 `--allow-unrelated-histories` 옵션을 추가하여 실행하는 것입니다.  

```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git pull origin master --allow-unrelated-histories
From https://github.com/hojinio/daelim_20202-2
 * branch            master     -> FETCH_HEAD
Merge made by the 'recursive' strategy.
 123456-4/hello.php | 2 ++
 123456/hello.php   | 2 ++
 2 files changed, 4 insertions(+)
 create mode 100644 123456-4/hello.php
 create mode 100644 123456/hello.php
```

연관성 없는 2개의 저장소가 강제로 history가 병합되어 pull이 된것을 확인할 수 있습니다.

```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ ls
123456  123456-4  hello.md
```

깃 로그를 확인해 봅니다.

```
infoh@hojin1 MINGW64 /e/git/test/pull (master)
$ git log
commit d61be6b28d6729e1e0608e7252eebea2dc87d908 (HEAD -> master)
Merge: f5f72fd 07bd439
Author: hojinlee <infohojin@gmail.com>
Date:   Wed Aug 26 17:52:11 2020 +0900

    Merge branch 'master' of https://github.com/hojinio/daelim_20202-2

commit f5f72fd6fb0c5fe2c107ed50aafdcc00d73159d6
Author: hojinlee <infohojin@gmail.com>
Date:   Wed Aug 26 16:58:28 2020 +0900

    hello

commit 07bd439f48ba00dbd389f4cc4025991ff7ece8c4 (origin/master)
Author: hojinlee <infohojin@gmail.com>
Date:   Tue Aug 25 16:25:18 2020 +0900

    hello 123456-4

commit 4588bfe2d987318773d436931f299701acad2c70
Author: hojinlee <infohojin@gmail.com>
Date:   Tue Aug 25 12:34:36 2020 +0900

    hello
```





