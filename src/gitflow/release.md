---
layout: home
title: "Git 교과서"
description: "버전 관리 시스템의 이해와 설치부터 커밋, 브랜치, 임시 처리, 병합, 복귀, 서브모듈, 태그까지
깃, 소스트리, 깃허브로 실습하며 기본기를 탄탄하게 다진다!"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---
# Release
<hr>
Release 브랜치는 개발 완료된 코드 버전을 배포하기 위한 전략입니다. 현재의 코드 상태가 최신으로 최종 사용자에게 배포할 수 있는 상태라면 release 브랜치를 생성합니다.

<br>

## 브랜치 의미
<hr>
Release는 develop와 master를 이어주는 중간 단계의 브랜치입니다. Release 전략은 깃랩-플로우의 production 브랜치 전략과 유사합니다. 또한, 테스트 과정의 pre-production 중간 단계의 브랜치와도 유사합니다. 

테스트가 완료되면 release는 master로 병합됩니다. master는 항상 안정적인 버전을 가지고 배포(deploy)할 수 있는 상태를 유지해야 합니다.

<br>

## 브랜치 생성
<hr>
Release 브랜치의 생성은 develop 브랜치를 기준으로 파생합니다. Release는 개발이 완료된 배포 버전이기 때문입니다.

개발된 코드를 테스트하고 완성된 배포하기 위해서 release 브랜치를 생성합니다. 깃-플로우 명령어로 쉽게 release 브랜치를 생성할 수 있습니다. 

![Release](./img/gitflow+release_01.png)

[명령어]
```
$ git flow release start 버전
```

새로운 배포 버전을 생성할 때는 start 옵션을 사용합니다. Release 브랜치를 생성할 때 브랜치 이름의 버전을 작성합니다. 

배포(release) 브랜치의 이름을 버전 형식으로 작성을 하는 이유는 브랜치 이름이 태그로 생성되기 때문입니다. 

> 배포용 브랜치를 생성할 때는 develop 브랜치 상에 있는 특정 커밋 ID를 지정할 수 있습니다. 특정 지정된 커밋 ID를 기반으로 release 브랜치를 생성합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (develop)
$ git flow release start '1.0.0'
Branches 'develop' and 'origin/develop' have diverged.
And local branch 'develop' is ahead of 'origin/develop'.
Switched to a new branch 'release/1.0.0'

Summary of actions:
- A new branch 'release/1.0.0' was created, based on 'develop'
- You are now on branch 'release/1.0.0'

Follow-up actions:
- Bump the version number now!
- Start committing last-minute fixes in preparing your release
- When done, run:

     git flow release finish '1.0.0'

infoh@DESKTOP MINGW64 /e/gitstudy13 (release/1.0.0)
```

브랜치를 목록을 확인해보겠습니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (release/1.0.0)
$ git branch -v
develop       d33afd4 new feature func1
  master        29990c7 first
* release/1.0.0 d33afd4 new feature func1 ☜ 체크아웃.
```

배포를 위한 release/1.0.0이 생성된 것을 확인할 수 있습니다. 또한, 자동으로 release 브랜치로 체크아웃됩니다. 배포 브랜치 또한 다음과 같이 `release/배포버전` 형태로 브랜치 이름이 정해지는 것을 확인할 수 있습니다.

<br>

## 테스트
<hr>
배포(release) 브랜치를 통하여 최종 버전을 생성하기 위한 테스트 과정을 수행할 수 있습니다. 테스트 과정에서 발생되는 버그들을 release 브랜치에서 수정할 수 있습니다. Release 브랜치에서는 작은 오류들 위주로 수정합니다. 

새로운 추가 기능을 개발할 때는 별개의 feature 브랜치에 작업한 후, 다른 배포(release) 버전으로 처리하는 것이 좋습니다.

배포의 테스트가 완료된 것으로 가정하여 코드를 조금 수정해봅니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (release/1.0.0)
$ code hello.htm ☜ VS Code를 실행합니다.
```

```html
<h1>깃 플로우 실습</h1>
<h2>새로운 feature 기능1 추가</h2>
<h3>현재 버전 1.0.0 으로 배포 가능합니다.</h3>
```

수정한 후 커밋도 같이 진행합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (release/1.0.0)
$ git commit -am "release test 1.0.0"
[release/1.0.0 58c6d46] release test 1.0.0
 1 file changed, 2 insertions(+), 1 deletion(-)
```

소스트리를 사용하여 생성된 커밋과 트리를 확인해봅니다.

![Release](./img/gitflow+release_02.png)

좀 더 확실한 배포를 위해서 release 브랜치 기반으로 테스트를 수행하는 것이 좋습니다. 실제적인 동작을 테스트하여 배포 시 발생될 수 있는 문제점들을 미리 방지합니다.

<br>

## 원격 배포
<hr>
배포를 준비하는 과정에서 다른 협업 개발자와 공동으로 테스트를 진행할 수 있습니다. 이런 경우 생성된 release 브랜치를 원격 저장소로 배포해야 합니다. 

Release 브랜치를 원격 저장소로 배포하기 위해서는 플로우의 publish 옵션을 사용합니다.

[명령어]
```
$ git flow release publish 버전
```

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (release/1.0.0)
$ git flow release publish 1.0.0
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 366 bytes | 183.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote:
remote: Create a pull request for 'release/1.0.0' on GitHub by visiting:
remote:      https://github.com/jinygit/gitstudy13/pull/new/release/1.0.0
remote:
To https://github.com/jinygit/gitstudy13.git
 * [new branch]      release/1.0.0 -> release/1.0.0 ☜ 원격 브랜치 생성
Branch 'release/1.0.0' set up to track remote branch 'release/1.0.0' from 'origin'.
Already on 'release/1.0.0'
Your branch is up to date with 'origin/release/1.0.0'.

Summary of actions:
- The remote branch 'release/1.0.0' was created or updated
- The local branch 'release/1.0.0' was configured to track the remote
branch
- You are now on branch 'release/1.0.0'
```

깃허브에서 브랜치 항목을 확인합니다. 3 branches로 변경된 것을 확인할 수 있습니다.

![Release](./img/gitflow+release_03.png)

배포된 브랜치를 통하여 다른 개발자와 협업 테스트를 진행할 수 있습니다.

<br>

## 브랜치 종료
<hr>
배포를 위한 테스트를 완료한 후에는 실제 배포를 해야 합니다. 테스트가 완성된 release를 안정된 마스터 브랜치로 병합합니다.

병합된 mastr 브랜치에서 배포를 위한 태그를 생성하고, 실제 배포를 진행합니다. 배포후에는 release 브랜치는 삭제합니다.

플로우 명령어의 finish 옵션을 이용하면 release와 master의 브랜치를 자동 병합합니다. 병합한 후에는 새로운 태그를 추가합니다. 기존 생성된 release도 삭제합니다.

finish 옵션은 배포를 위한 일련의 작업들을 한 번에 수행합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (release/1.0.0)
$ git flow release finish 1.0.0
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Merge made by the 'recursive' strategy. ☜ 병합
 hello.htm | 4 +++-
 1 file changed, 3 insertions(+), 1 deletion(-)
Already on 'master'
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)
Switched to branch 'develop'
Your branch is up to date with 'origin/develop'.
Merge made by the 'recursive' strategy.
 hello.htm | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)
To https://github.com/jinygit/gitstudy13.git
 - [deleted]         release/1.0.0 ☜ 브랜치 삭제
Deleted branch release/1.0.0 (was 58c6d46).

Summary of actions:
- Release branch 'release/1.0.0' has been merged into 'master'
- The release was tagged '1.0.0'
- Release tag '1.0.0' has been back-merged into 'develop'
- Release branch 'release/1.0.0' has been locally deleted; it has been remotely deleted from 'origin'
- You are now on branch 'develop'
```

release 브랜치를 종료하면 2개의 메시지 입력을 요청합니다. Master로 병합을 위한 메시지와 태그의 생성을 위한 메시지입니다.
 
① 병합 메시지를 작성합니다.
```
Merge branch 'release/1.0.0'

# Please enter a commit message to explain why this merge is necessary,
# especially if it merges an updated upstream into a topic branch.
#
# Lines starting with '#' will be ignored, and an empty message aborts
# the commit.
```

② 태그 메시지를 작성합니다.
```
#
# Write a message for tag:
#   1.0.0
# Lines starting with '#' will be ignored.
```

Vi 에디터를 사용하여 메시지를 작성합니다. 작성 후 저장 및 종료하세요. 병합 후에는 다시 develop 브랜치로 돌아옵니다. 브랜치를 목록을 확인합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (develop)
$ git branch -v
* develop 060ff55 [ahead 3] Merge tag '1.0.0' into develop
master  5f40326 [ahead 3] Merge branch 'release/1.0.0'
```

소스트리를 통하여 결과를 확인합니다.

![Release](./img/gitflow+release_04.png)

새로운 병합이 이루어진 것을 확인할 수 있습니다. 배포가 완료되면 release 브랜치도 자동으로 삭제됩니다. 

release 브랜치는 배포가 완료되면 자동으로 태그를 추가합니다. tag 명령어를 통하여 생성된 태그를 확인합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (develop)
$ git tag
1.0.0

infoh@DESKTOP MINGW64 /e/gitstudy13 (develop)
$ git tag -v 1.0.0
object 5f40326d8133e8db5e20e3ee73113be69e742ce8
type commit
tag 1.0.0
tagger hojin <infohojin@gmail.com> 1559380711 +0900

release 1.0.0:
error: no signature found
```

새로운 태그가 생성된 것을 확인할 수 있습니다. 

![Release](./img/gitflow+release_05.png)

<br>

## 직접 배포
<hr>
로컬 저장소는 release 브랜치를 이용하여 새로운 배포 버전이 생성되었습니다. 하지만 아직 새로운 배포 버전은 원격 저장소에 등록되지 않았습니다.

브랜치의 목록을 확인합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (develop)
$ git branch -v
* develop 060ff55 [ahead 3] Merge tag '1.0.0' into develop
master  5f40326 [ahead 3] Merge branch 'release/1.0.0'
```

ahead 3로 원격 저장소에 푸시할 내용들이 남아 있습니다.

① 푸시를 통하여 원격 저장소에 개발 브랜치를 갱신해줍니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (develop)
$ git push -u origin develop
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 665 bytes | 133.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/jinygit/gitstudy13.git
   d33afd4..060ff55  develop -> develop
Branch 'develop' set up to track remote branch 'develop' from 'origin'.

infoh@DESKTOP MINGW64 /e/gitstudy13 (develop)
$ git branch -v
* develop 060ff55 Merge tag '1.0.0' into develop
master  5f40326 [ahead 3] Merge branch 'release/1.0.0'
```

아직 master 브랜치도 푸시할 내용이 남아 있습니다.

② 마스터 브랜치로 체크아웃합니다. 마스터 브랜치로 갱신합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (develop)
$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)

infoh@DESKTOP MINGW64 /e/gitstudy13 (master)
$ git push -u origin master
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/jinygit/gitstudy13.git
   29990c7..5f40326  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

infoh@DESKTOP MINGW64 /e/gitstudy13 (master)
$ git branch -v
  develop 060ff55 Merge tag '1.0.0' into develop
* master  5f40326 Merge branch 'release/1.0.0'
```

③ 태그 정보를 서버로 전송합니다. 
변경된 모든 브랜치의 정보가 원격 저장소로 푸시되었습니다. 하지만 생성된 태그의 정보는 아직 원격 저장소로 전송되지 않았습니다.

태그의 전송은 별도의 푸시 옵션을 이용하여 실행해야 합니다. --tags 옵션을 같이 사용하여 한 번 더 원적 저장소로 전송합니다.

```bash
infoh@DESKTOP MINGW64 /e/gitstudy13 (master)
$ git push --tags
Enumerating objects: 1, done.
Counting objects: 100% (1/1), done.
Writing objects: 100% (1/1), 157 bytes | 78.00 KiB/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/jinygit/gitstudy13.git
 * [new tag]         1.0.0 -> 1.0.0 ☜ 태그 배포
```

깃허브의 저장소를 확인해봅니다. 새롭게 추가한 태그 정보를 확인할 수 있습니다. release 부분이 1로 변경된 것을 확인할 수 있습니다. 깃허브의 release 부분을 클릭해봅니다.

![Release](./img/gitflow+release_06.png)

<br><br>