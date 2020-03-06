
8장

병합과 충돌

깃은 언제든지 새로운 작업을 할 수 있는 브랜치를 만들 수 있습니다. 브랜치는 원본을 유지한 채로 새로운 기능을 개발하거나 버그를 수정하는 작업을 할 수 있는 기능입니다. 브랜치로 분기하여 코드를 수정했다면 언젠가는 원본에 다시 변경된 코드를 적용해야 합니다. 이 장에서는 파생된 브랜치 2개를 하나로 합치는 방법을 알아보겠습니다.

8.1 병합

8.2 Fast-Forward 병합

8.3 3-way 병합

8.4 브랜치 삭제

8.5 충돌

8.6 브랜치 병합 여부 확인

8.7 리베이스

8.8 정리

 

QUICK GUIDE

Fast-Forward 병합

330136.png
3-way 병합

330165.png
 

병합(리베이스)

330217.png
8.1

307449.png
307496.png
병합

git

 

브랜치를 생성하는 목적은 원본 코드에 영향을 주지 않고 분리하여 개발하기 위해서입니다. 독립된 브랜치에서 개발 작업이 끝나면 다시 원본 브랜치에 작업한 결과를 반영해야 합니다. 분리된 브랜치를 한 브랜치로 합치는 작업을 병합(합치기)이라고 합니다. 두 코드를 하나씩 직접 비교해 가며 수동으로 병합하거나 깃 같은 도구를 사용하여 자동으로 병합할 수 있습니다.

8.1.1 하나씩 직접 비교하는 수동 병합

소스 코드가 2개 있다고 합시다. 하나는 원본 소스 코드고, 또 하나는 수정된 소스 코드입니다. 수정된 코드는 버그를 고치고, 새로운 기능을 적용하여 테스트한 코드입니다. 개발을 끝내고 테스트를 완료했다면 수정 내역을 원본 소스 코드에 모두 반영해 주어야 합니다. 또는 수정된 코드 자체로 원본 코드를 대체할 수도 있습니다.

수동으로 병합하려면 양쪽 파일을 일일이 비교하며 바뀐 점을 찾아서 적용해야 합니다. 하지만 오류 없이 코드를 병합하는 것은 간단하지 않습니다. 몇 줄 안 되는 코드라면 몰라도 실제 개발할 때는 수천 줄 이상이기 때문에 두 코드를 하나로 합치는 것은 매우 힘든 작업입니다. 또 사람의 기억력은 한계가 있기 때문에 며칠 동안 작업한 내용을 일일이 옮겨 적는 것도 힘듭니다.

소스 코드가 2개보다 많다면 어떻게 될까요? 예를 들어 원본 소스 A를 복제하여 B를 수정하고, B를 복제하여 C도 수정하고 있습니다. 요즘은 협업 때문에 다수 개발자가 각각 새로운 기능들을 만듭니다. 또 365일 24시간 분업화된 상태에서 생긴 버그는 여러 개발자가 수정합니다. 이처럼 여러 개발자와 코드를 공유하면서 변경된 소스 코드를 병합하는 것은 매우 복잡합니다.

 

311277.jpg 그림 8-1 코드 수동 병합

316128.png 

수정이 완료되면 B는 원본 소스 A에 수정 내역을 반영하는 작업을 해야 하고, C 또한 B를 반영하여 수정된 원본 소스 A에 또다시 수정 작업을 반영해야 합니다. 병합하려면 코드의 변경된 시점을 기억해야 합니다. 변경된 시점을 기준으로 순차적으로 병합 처리를 하는 것이 좀 더 쉽습니다. 변경된 시간 순서를 따르지 않고 병합하면 코드가 엉켜 잘못 동작할 확률이 높습니다.

8.1.2 깃으로 자동 병합

숙련된 개발자라고 해도 복잡한 수정 내역을 순차적인 시간에 따라 병합하는 것은 쉬운 일이 아닙니다. 깃을 사용하면 복잡한 파일을 좀 더 간편하게 병합할 수 있습니다.

물론 깃이 모든 코드를 완벽하게 병합하는 것은 아닙니다. 아무리 좋은 도구라고 해도 자동으로 반영하지 못하는 것들이 있습니다. 이를 충돌이라고 합니다. 충돌은 8.5절에서 자세히 알아볼 것입니다.

Note

line.jpg
line.jpg
line.jpg
315121.png
 

깃의 자동 병합은 원본을 기준으로 두 파일의 변경 이력을 비교합니다. 변경된 파일 내용이 발견되면 자동으로 수정된 코드 내용을 병합합니다.

깃의 병합은 브랜치를 기준으로 합니다. 브랜치는 같은 저장소 내에서 서로 독립적으로 작업을 분리한 영역입니다. 분리된 각각의 브랜치에서 수정된 사항을 하나의 브랜치로 병합합니다. 병합하고자 하는 브랜치는 같은 로컬 저장소에 있어야 합니다.

과거에는 모든 병합 작업을 수동으로 해서 어려웠지만, 이제는 이러한 수동 병합 작업을 깃이 대신 처리합니다. 하지만 깃이 모든 코드의 병합을 완벽하게 처리할 수는 없습니다. 아무리 좋은 도구라고 해도 자동으로 반영하지 못하는 것들이 있습니다. 이를 충돌이라고 합니다.

8.1.3 병합 방식

깃의 병합은 브랜치를 기반으로 실행합니다. 각 브랜치를 비교하여 자동 병합하는 형태입니다. 따라서 병합하려면 브랜치를 만들어 브랜치 안에서 수정 작업을 해야 합니다. 사실 파일을 병합하는 것은 그렇게 간단한 일이 아닙니다. 어떤 내용을 수정했고, 새로 추가했는지 판별하기가 어렵기 때문입니다. 병합할 때는 상대적인 기준을 판별하는 알고리즘들이 존재합니다. 이 알고리즘들은 기준점과 수정 사항을 병합하는 처리 로직에 따라 다릅니다.

깃은 병합을 위해 두 가지 기본적인 알고리즘 방식을 제공합니다. 깃에서 충돌 없이 병합하려면 이 두 가지 병합 방식의 차이를 알아야 합니다.

● Fast-Forward 병합
● 3-way 병합
두 방식으로 실습하기 전에 미리 별도의 저장소를 생성해 두겠습니다.

$ cd 실습폴더

$ mkdir gitstudy08

320113.png
새 폴더 만들기

$ cd gitstudy08

320146.png
만든 폴더로 이동

 

infoh@DESKTOP MINGW64 /e/gitstudy08

$ git init

320176.png
저장소 초기화

Initialized empty Git repository in E:/gitstudy08/.git/

그리고 index.htm 파일을 만들어 코드를 입력하고 저장합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ code index.htm

320206.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<h1>hello GIT world!</h1>

</body>

</html>

 

파일을 등록하고 첫 번째 커밋을 합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git add .

320236.png
전체 파일을 등록. 추적 상태

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git commit -m "first"

346314.png
커밋

[[master (root-commit) f123d5c] first

1 file changed, 11 insertions(+)

create mode 100644 index.htm

이 과정을 그림으로 표현하면 다음과 같습니다.

311279.jpg 그림 8-2 파일 등록 및 첫 번째 커밋

316134.png 

앞에서 병합하려면 모든 브랜치가 단일 저장소에 있어야 한다고 했습니다. 같은 저장소의 브랜치를 병합할 수 있다는 점을 잊지 마세요!

8.2

307535.png
307582.png
Fast-Forward 병합

git

 

깃의 가장 간단한 브랜치 병합은 Fast-Forward 방식입니다. 영어 표현을 풀어 쓰면 빨리 감기라고 할 수 있습니다. 일반적으로 Fast-Forward 병합 방식은 혼자 개발할 때 사용합니다.

혼자 개발할 때는 브랜치가 생성된 커밋에 따라 순차적으로 분기됩니다. 또 코드 수정도 순차적으로 할 때가 많습니다. 즉, 브랜치가 분기되지만 전체 커밋 그림으로 보면 모든 변경 사항은 순차적으로 진행됩니다. 이러한 순차적 커밋에 맞추어 병합을 처리하는 방법이 Fast-Forward 병합입니다.

 

8.2.1 브랜치 생성과 수정 작업

실습을 위해 새로운 feature 브랜치를 생성하겠습니다. 그리고 feature 브랜치로 체크아웃합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git branch feature

320266.png
브랜치 생성

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

346347.png
브랜치 변경

$ git checkout feature

320296.png
브랜치 이동

Switched to branch 'feature'

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

브랜치를 생성할 때 분기 기준은 master의 최종 커밋 포인터입니다. 포인터를 확인할 수 있는 rev-parse 명령어로 확인해 봅시다. 첫 번째 커밋 f123d5c와 값이 동일합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

$ git rev-parse feature

346379.png
브랜치 커밋 확인

f123d5c9fd0c1f8a2f4ec86f63451a179371ae09

이 내용은 다음과 같이 나타낼 수 있습니다.

311281.jpg 그림 8-3 브랜치 생성

316136.png 

소스트리에서 생성된 브랜치를 확인할 수 있습니다. 이 장에서는 깃 배시와 소스트리를 번갈아 가며 실습을 합니다. 먼저 소스트리의 새 탭에서 Add 버튼을 클릭합니다. 탐색을 눌러 앞에서 만든 gitstudy08 폴더를 찾아 선택한 후 추가를 누릅니다. 그러면 gitstudy08 저장소와 연결됩니다.

생성한 feature 브랜치를 클릭하면 feature 브랜치와 master 브랜치의 시작 위치가 동일한 것을 확인할 수 있습니다.

311068.jpg 그림 8-4 소스트리에서 브랜치 위치 확인

0804.jpg 

생성한 feature 브랜치 안에 있는 index.htm 파일을 수정하겠습니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

$ code index.htm

320327.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

</header>

<h1>hello GIT world!</h1>

</body>

</html>

 

코드에 <header></header> 태그를 삽입하고 저장합니다. 기존 코드를 수정했기 때문에 파일 상태는 modified로 변경됩니다. 다음과 같이 수정한 파일을 커밋합니다. -a 옵션과 같이 사용하면 스테이지 영역을 추가하면서 동시에 커밋을 할 수 있습니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

$ git commit -am "add header"

346587.png
등록 및 커밋

[feature 3f7799f] add header

1 file changed, 2 insertions(+)

이 과정을 그림으로 나타내면 다음과 같습니다.

311283.jpg 그림 8-5 브랜치 수정 및 커밋 이동

316153.png 

소스트리에서 커밋 로그를 확인해 보겠습니다. feature 브랜치가 master 브랜치보다 커밋이 하나 더 있는 것을 볼 수 있습니다.

311070.jpg 그림 8-6 소스트리에서 커밋 위치 확인

0806.jpg 

실습을 위해 수정과 커밋을 몇 번 더 합시다. 이번에는 <header> 코드 안에 <ul><li> 태그를 추가하여 두 번 커밋할 것입니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

$ code index.htm

346626.png
VS Code 실행(수정 1)

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

</ul>

</header>

<h1>hello GIT world!</h1>

</body>

</html>

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

$ git commit -am "add menu1"

346658.png
등록 및 커밋

[feature e762475] add menu1

1 file changed, 3 insertions(+)

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

$ code index.htm

346688.png
VS Code 실행(수정 2)


index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

</ul>

</header>

<h1>hello GIT world!</h1>

</body>

</html>

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

$ git commit -am "add menu2"

346718.png
등록 및 커밋

[feature 7caf5f0] add menu2

1 file changed, 1 insertion(+)

지금까지 과정을 그림으로 나타내면 다음과 같습니다.

311285.jpg 그림 8-7 브랜치 생성 후 추가 커밋 진행 상태

316171.png 

feature 브랜치에 추가된 커밋 로그를 확인해 봅시다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

$ git log

346748.png
로그 확인

commit 7caf5f028ba013f1eb74e2f6c8cc400c02b0eb9c (HEAD -> feature)

Author: hojin <infohojin@gmail.com>

Date: Thu May 16 16:54:30 2019 +0900

add menu2

 

commit e76247541b07357220b042450aaf4a8aae037342

Author: hojin <infohojin@gmail.com>

Date: Thu May 16 16:53:55 2019 +0900

add menu1

 

commit 3f7799fb86b2b9abd980c26b1b2f33791e6708cf

Author: hojin <infohojin@gmail.com>

Date: Thu May 16 16:45:42 2019 +0900

add header

 

commit f123d5c9fd0c1f8a2f4ec86f63451a179371ae09 (master)

Author: hojin <infohojin@gmail.com>

Date: Thu May 16 16:14:38 2019 +0900

first

소스트리에서 브랜치의 커밋 로그를 확인해 보면, feature 브랜치가 master 브랜치에서 분리되어 header, menu1, menu2 커밋 작업을 세 번 수행한 것을 확인할 수 있습니다.

311072.jpg 그림 8-8 feature 브랜치에 세 번 커밋됨

0808.jpg 

우리는 브랜치를 만들어 feature 브랜치에 기능을 추가했습니다. 하지만 소스트리에서 브랜치를 확인하면 브랜치 경로가 일직선으로 1개만 있습니다. 서로 다른 브랜치이지만 순차적으로 커밋을 했기 때문에 일직선으로 보이는 것입니다. 이러한 모양의 브랜치에서 병합 작업을 할 때는 Fast-Forward 방식의 알고리즘이 적용됩니다.

8.2.2 병합 위치

깃의 merge 명령어는 브랜치를 병합합니다. merge 명령어는 현재 브랜치를 기준으로 다른 브랜치의 모든 커밋을 병합합니다.

$ git merge 브랜치이름

 

브랜치를 병합하려면 기준과 대상이 있어야 합니다. 기준은 체크아웃된 현재 브랜치입니다. 따라서 병합하려면 먼저 기준이 되는 브랜치로 이동해야 합니다. 우리는 master 브랜치에서 feature 브랜치로 분기하여 작업했습니다. 작업한 feature 브랜치를 다시 master 브랜치로 병합할 것입니다. 병합을 하려면 먼저 master 브랜치로 체크아웃해야 합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (feature)

$ git checkout master

320360.png
기준 브랜치로 이동

Switched to branch 'master'

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

병합을 할 수 있게 기준 브랜치(master 브랜치)로 이동했습니다.

311287.jpg 그림 8-9 병합을 할 수 있게 기준 브랜치로 이동

316187.png 

master 브랜치로 체크아웃한 상태에서 파일(코드)을 확인해 봅시다. feature 브랜치에서 작업한 내용이 사라졌습니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ code index.htm

346802.png
VS Code 실행(코드 확인)

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<h1>hello GIT world!</h1>

</body>

</html>

 

원본의 master 브랜치에서 작업한 내용만 출력됩니다. 이처럼 브랜치는 기존 원본을 유지한 상태에서 서로 간섭하지 않고 feature 브랜치에서 코드를 수정할 수 있습니다. 이제 feature 브랜치에서 작업한 내용을 병합해 보겠습니다.

8.2.3 Fast-Forward 병합 적용

커밋 작업은 분기된 feature 브랜치에서 모두 수행했습니다. 아직 master 브랜치에는 추가된 커밋이 없습니다. 이러한 상태에서 두 브랜치를 병합합시다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git merge feature

320390.png
feature 브랜치 병합

Updating f123d5c..7caf5f0

Fast-forward

320420.png
병합 방식 표시

index.htm | 6 ++++++

1 file changed, 6 insertions(+)

feature 브랜치의 커밋을 master 브랜치에 병합했습니다. 병합 메시지를 확인해 볼까요? 메시지에 Fast-Forward 방식을 사용하여 병합했다고 출력됩니다.

이 과정을 그림으로 나타내면 다음과 같습니다.

311290.jpg 그림 8-10 병합한 후 커밋 구조

316190.png 

이 그림처럼 feature 브랜치의 커밋들이 하나씩 master 브랜치로 병합합니다. master 브랜치에는 커밋이 하나도 없기 때문에 feature 브랜치가 master 브랜치로 이동한 것처럼 보입니다. 소스트리에서 병합 결과를 확인합니다.

 

311074.jpg 그림 8-11 소스트리에서 병합 결과 확인

0811.jpg 

이처럼 병합한 후에는 master 브랜치의 마지막 커밋 위치와 feature 브랜치의 마지막 커밋 위치가 같습니다. 동일한 HEAD 포인터를 가지게 됩니다.

log 명령어로 커밋 기록을 확인합시다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git log -1

346834.png
로그 확인

commit 7caf5f028ba013f1eb74e2f6c8cc400c02b0eb9c (HEAD -> master, feature)

Author: hojin <infohojin@gmail.com>

Date: Thu May 16 16:54:30 2019 +0900

add menu2

Fast-Forward 병합은 작업한 브랜치를 원본 브랜치에 병합할 때 작업한 브랜치의 시작 커밋을 원본 브랜치 이후의 커밋으로 가리킵니다. 이는 단순히 커밋 위치를 최신으로 옮기는 것과 비슷합니다.

Fast-Forward 병합을 잘했는지 결과를 확인해 봅시다. master 브랜치의 원본 파일에 feature 브랜치에서 수정한 내용이 반영되어 있으면 잘 병합한 것입니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ code index.htm

346864.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

 

<li>깃소개</li>

<li>깃설치</li>

</ul>

</header>

<h1>hello GIT world!</h1>

</body>

</html>

 

master 브랜치의 index.htm 파일을 확인해 보니 잘 병합했네요. Fast-Forward 병합은 병합할 하나의 브랜치 파일을 기준 브랜치로 복사하여 수정된 파일을 원본에 그대로 적용한 것과 같습니다. 즉, 원본에 추가된 내용이 없다는 가정하에 변경한 파일을 대체하는 것입니다.

8.3

307617.png
307664.png
3-way 병합

git

 

이번에는 깃의 또 다른 병합 알고리즘인 3-way 방식을 알아보겠습니다. 3-way 병합은 좀 더 복잡한 병합을 처리할 수 있는 방법입니다. 여러 개발자와 협업으로 작업하는 경우 대부분 3-way 병합을 사용합니다.

8.3.1 브랜치 생성과 수정 작업

직접 실습하며 3-way 병합을 익히겠습니다. 새로운 작업을 할 hotfix 브랜치를 생성하고, hotfix 브랜치로 체크아웃합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

346997.png
이동

$ git checkout -b hotfix

346898.png
브랜치 생성

Switched to a new branch 'hotfix'

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)

현재 브랜치 위치는 hotfix입니다.

311292.jpg 그림 8-12 hotfix 브랜치 생성

316240.png 

이번에는 소스 코드에 <footer></footer> 태그를 추가하고 내용을 적을 것입니다. 커밋 두 번으로 나누어 진행합니다. 먼저 <footer> 태그를 추가하고 저장합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)

$ code index.htm

346930.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

</ul>

</header>

<h1>hello GIT world!</h1>

<footer>

</footer>

</body>

</html>

 

수정한 파일은 Modified 상태가 됩니다. 수정한 파일을 다시 스테이지에 등록한 후 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)

$ git commit -am "add footer"

346961.png
등록 및 커밋

[hotfix c5df346] add footer

1 file changed, 3 insertions(+)

다시 index.htm 파일에 <footer> 내용을 추가한 후 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)

$ code index.htm

347027.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

</ul>

</header>

<h1>hello GIT world!</h1>

<footer>

copyright all right 2020 reserved by hojinlee

</footer>

</body>

</html>

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)

$ git commit -am "add copyright"

347058.png
등록 및 커밋

[hotfix 7277f2d] add copyright

1 file changed, 1 insertion(+)

이 과정을 그림으로 나타내면 다음과 같습니다.

311295.jpg 그림 8-13 hotfix 브랜치에서 파일 수정 및 커밋 로그

316244.png 

소스트리에서 커밋 로그 기록을 확인하면 다음과 같습니다.

311076.jpg 그림 8-14 소스트리에서 hotfix 브랜치의 커밋 로그 확인

0814.jpg 

hotfix 브랜치에 새로운 커밋이 2개 추가되었습니다. 지금까지 hotfix 브랜치에서 진행한 수정은 앞에서 실습한 Fast-Forward 병합과 유사합니다. Fast-Forward 병합에서는 생성한 브랜치에만 수정과 커밋을 했고, 원본 master 브랜치에서는 어떤 작업도 하지 않았습니다.

8.3.2 마스터 변경

이번에는 브랜치 모양을 변경해 보겠습니다. master 브랜치에도 새로운 커밋을 추가하여 실습을 진행하겠습니다. 먼저 hotfix 브랜치에서 master 브랜치로 이동합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (hotfix)

$ git checkout master

347105.png
브랜치 이동

Switched to branch 'master'

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

320451.png
원본 브랜치로 이동

311297.jpg 그림 8-15 원본 브랜치로 이동

316284.png 

hotfix 브랜치의 마지막 커밋은 7277f2d입니다. 그리고 master 브랜치의 마지막 커밋은 7caf5f0입니다. 시간적으로 좀 더 앞 단계인 master 브랜치에 새로운 커밋을 추가해 보겠습니다.

 

master 브랜치의 index.htm 파일에 menu3을 추가하고 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ code index.htm

347137.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

</ul>

</header>

<h1>hello GIT world!</h1>

</body>

</html>

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git commit -am "add menu3"

347168.png
등록 및 커밋

[master 49c98a1] add menu3

1 file changed, 1 insertion(+)

다시 한 번 menu4를 추가하고 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ code index.htm

347198.png
VS Code 실행

 

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

<li>브랜치</li>

</ul>

</header>

<h1>hello GIT world!</h1>

</body>

</html>

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git commit -am "add menu4"

347228.png
등록 및 커밋

[master 8583edf] add menu4

1 file changed, 1 insertion(+)

이제 메뉴가 4개입니다. master 브랜치에 추가 커밋이 발생하면 다음과 같이 브랜치는 7caf5f0을 기준으로 hotfix와 master 브랜치로 갈라집니다. 기준 커밋에서 서로 다른 브랜치의 커밋이 연결됩니다.

311300.jpg 그림 8-16 기준 커밋에서 분기

316286.png 

소스트리에서 master 브랜치의 그래프 모양을 확인해 보겠습니다. 이전 Fast-Forward 병합과는 달리 브랜치가 좀 더 확실하게 나뉘어 있습니다.

311078.jpg 그림 8-17 소스트리에서 브랜치 그래프 확인

0817.jpg 

8.3.3 공통 조상

앞의 실습에서 브랜치별로 각각 커밋하면 두 브랜치로 갈라지는 모습을 보았습니다. 이처럼 브랜치 모양이 갈라지는 형태로 나뉠 때는 Fast-Forward 방식의 알고리즘을 적용하여 병합할 수 없습니다. 이때는 다른 병합 알고리즘인 3-way 방식을 이용해야 합니다.

두 브랜치를 병합하려면 먼저 분할 기준인 공통 커밋을 찾아야 합니다. 이를 공통 조상 커밋이라고 합니다. 공통 조상 커밋을 포함하는 브랜치와 새로운 두 브랜치, 이렇게 3개를 하나로 병합해야 합니다. 브랜치가 3개 있다고 해서 3-way 병합이라고 합니다.

311302.jpg 그림 8-18 브랜치 3개 병합

316340.png 

깃은 3-way 병합을 할 때 공통 조상 커밋을 자동으로 찾아 줍니다. 이는 다른 VCS들보다 서로 다른 브랜치를 편리하게 병합할 수 있는 깃의 장점입니다.

8.3.4 병합 커밋

병합은 각 브랜치에서 독립적으로 작업된 소스를 파일 하나로 결합합니다. 하지만 브랜치별로 각각 작업한 내용을 병합하는 과정은 힘들고 어렵습니다. 하지만 깃을 사용하면 복잡한 병합도 좀 더 손쉽게 처리할 수 있습니다.

3-way 병합은 두 브랜치에서 공통 조상 커밋을 자동으로 찾아 주며, 공통 조상 커밋을 기준으로 브랜치를 병합합니다. 그리고 병합을 성공적으로 완료한 후에는 새로운 커밋을 추가로 하나 생성합니다. 새로 생성된 커밋을 병합 커밋이라고 합니다. 병합 커밋은 부모 커밋이 2개라는 특징이 있습니다.

311304.jpg 그림 8-19 병합 커밋

316342.png 

그럼 앞에서 실습한 hotfix 브랜치를 master 브랜치에 병합해 봅시다. hotfix 브랜치를 병합하려면 먼저 기준이 되는 master 브랜치로 체크아웃해야 합니다. 다른 브랜치에 있다면 git checkout master로 체크아웃하세요.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

320481.png
기준 브랜치

$ git merge hotfix

320513.png
기준 브랜치에 hotfix 병합

Auto-merging index.htm

Merge made by the 'recursive' strategy.

347269.png
3-way 병합

index.htm | 3 +++

1 file changed, 3 insertions(+)

3-way 방식으로 hotfix 브랜치와 master 브랜치를 병합했습니다. 그림으로 병합 구조를 나타내면 그림 8-20과 같습니다.

311307.jpg 그림 8-20 hotfix 브랜치의 3-way 병합

316344.png 

성공적으로 병합한 후에는 커밋 로그를 확인합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git log -1

347302.png
로그 확인

commit a48d563373f777f5f19a1ad9426297c5bc31d01c (HEAD -> master)

Merge: 8583edf 7277f2d

Author: hojin <infohojin@gmail.com>

Date: Fri May 17 16:30:07 2019 +0900

Merge branch 'hotfix'

새로운 병합 커밋이 하나 추가되었습니다. 소스트리에서도 병합된 모습을 확인할 수 있습니다.

311080.jpg 그림 8-21 소스트리에서 병합 커밋 확인

0821.jpg 

8.3.5 병합 메시지

3-way 병합을 간단히 실습해 보았습니다. 앞에서 3-way 병합을 할 때 새로운 병합 커밋이 생성되었습니다. 3-way 병합은 Fast-Forward 병합과 달리 병합 메시지가 필요합니다. 그리고 “Merge branch ‘hotfix’”라고 커밋 메시지가 자동 삽입된 것을 확인할 수 있습니다. 깃은 두 브랜치를 병합한 후에 새로운 커밋을 하면서 동시에 메시지를 자동 생성합니다.

자동으로 작성되는 메시지 외에 직접 커밋 메시지를 작성할 수도 있습니다. merge 명령어를 실행할 때 -e 또는 --edit 옵션을 사용하면 됩니다.

$ git merge 브랜치이름 --edit

 

그럼 직접 병합 메시지를 작성해 봅시다. 실습을 위해 바로 앞에서 진행한 병합을 취소하고 메시지를 추가하여 다시 병합하겠습니다. reset 명령어로 바로 앞의 병합을 취소할 수 있습니다. 리셋은 9장에서 자세히 설명하겠습니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git reset --hard HEAD^

320578.png
병합 취소

HEAD is now at 8583edf add menu4

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git merge hotfix --edit

347332.png
병합 명령

개발자가 직접 입력할 수 있는 vi 에디터 창이 열립니다.

311082.jpg 그림 8-22 병합 메시지를 입력할 수 있는 vi 에디터 창

0822.jpg
330489.png
Merge branch 'hotfix'

 

# Please enter a commit message to explain why this merge is necessary,

# especially if it merges an updated upstream into a topic branch.

#

# Lines starting with '#' will be ignored, and an empty message aborts

# the commit.

~

~

~

E:/gitmerge/.git/MERGE_MSG [unix] (19:09 17/01/2019) 1,1 모두

" E:/gitmerge/.git/MERGE_MSG [유닉스] 7L, 249C

 

 

병합 메시지를 작성하고 에디터를 종료합니다. 그러면 다음과 같이 병합 결과 메시지가 출력되고 직접 작성한 메시지로 커밋됩니다.

Auto-merging index.htm

Merge made by the 'recursive' strategy.

index.htm | 3 +++

1 file changed, 3 insertions(+)

8.4

307699.png
307746.png
브랜치 삭제

git

 

브랜치를 병합한 후에는 병합한 브랜치를 어떻게 관리할지 결정해야 합니다. 일반적으로 병합한 이후에는 병합된 브랜치를 삭제합니다. 하지만 지속적인 통합과 개발을 해야 하는 브랜치라면 병합 후에도 계속 남겨 둡니다.

깃 플로

깃 플로(git flow)는 브랜치 관리 기법입니다. 수많은 브랜치 작업을 규격화해서 브랜치를 쉽게 다룰 수 있도록 하는 전략이라고 생각하면 됩니다. 깃 플로에는 기본적으로 master, feature, develop, release, hotfix 브랜치가 있습니다. 이 중에서 develop 브랜치는 master 브랜치에 병합한 후에도 삭제하지 않고 계속 유지합니다. 이처럼 오랫동안 유지하는 브랜치를 long-running 브랜치라고 합니다.

Note

line.jpg
line.jpg
line.jpg
315279.png
 

8.4.1 병합 후 삭제

병합된 브랜치의 커밋은 모두 원본 브랜치에 적용됩니다. 따라서 중복되는 커밋을 가지는 별도의 브랜치를 유지할 필요는 없습니다. 불필요한 브랜치는 삭제합니다.

$ git branch -d 브랜치이름

 

브랜치를 삭제할 때는 -d 옵션을 사용합니다. 참고로 -d 옵션은 병합을 완료한 브랜치만 삭제할 수 있습니다. 따라서 실습에서 성공적으로 병합한 feature 브랜치는 -d 옵션으로 삭제할 수 있습니다. master 브랜치에 병합된 hotfix 브랜치를 삭제하겠습니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git branch -d hotfix

320609.png
브랜치 삭제

Deleted branch hotfix (was 7277f2d).

병합을 완료하지 않은 브랜치를 삭제하고 싶다면 대문자 -D 옵션을 사용해야 합니다.1

8.5

307793.png
307840.png
충돌

git

 

실습을 그대로 따라 했다면 모든 병합을 성공적으로 처리했을 것입니다. 하지만 실제 개발 환경에서는 실습과 달리 다양한 문제가 발생합니다. 대표적으로 여러 사람과 개발한 코드 일부분이 충돌(complicit)하는 경우입니다. 보통 충돌은 3-way 병합이 실패한 경우입니다.

8.5.1 충돌이 생기는 상황

여러 사람과 개발 작업을 하다 보면 예상외로 충돌이 자주 발생합니다. 대부분의 충돌 원인은 같은 위치의 코드를 동시에 수정했기 때문입니다. 파일을 수정할 때 여러 개발자가 서로 다른 위치를 수정했다면 깃에서 서로 다른 위치의 소스를 자동으로 병합하기 때문에 문제가 없습니다. 하지만 파일에서 동일한 위치에 두 명 이상이 서로 다르게 수정했다면 충돌이 발생합니다.

즉, 같은 위치를 동시에 수정하면 두 수정 중 어떤 것이 맞는지 깃에서 자동으로 알 수 없기 때문에 충돌이 발생합니다. 이때 깃은 충돌 오류라고 알려 주고, 개발자에게 직접 수정하여 충돌을 해결하라고 요청합니다. 이러한 병합 충돌은 상당히 자주 발생합니다.

8.5.2 실습을 위한 충돌 만들기

실습을 위해 인위적인 충돌 상황을 만들어 보겠습니다. 새로운 footer 브랜치를 만들고 체크아웃합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

320640.png
기준 브랜치

$ git checkout -b footer

320672.png
기준에서 새로운 브랜치 파생

Switched to a new branch 'footer'

독립된 footer 브랜치에서 index.htm 파일의 <footer>~</footer> 부분 코드를 수정하고 커밋하겠습니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (footer)

$ code index.htm

347365.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

</ul>

</header>

<h1>hello GIT world!</h1>

<footer>

copyright all right 2018 reserved

by hojinlee

</footer>

</body>

</html>

 

카피라이터 부분을 두 줄로 수정했습니다. 이어서 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (footer)

$ git commit -am "edit footer"

347395.png
등록 및 커밋

[footer d141624] edit footer

1 file changed, 1 insertion(+)

그림으로 나타내면 다음과 같습니다.

311309.jpg 그림 8-23 footer 브랜치 생성 및 수정

316406.png 

이번에는 다시 master 브랜치로 체크아웃하여 index.htm 파일을 수정합니다. 충돌이 발생하도록 동일한 위치의 내용을 수정하고 커밋하겠습니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (footer)

$ git checkout master

347425.png
브랜치 이동

Switched to branch 'master'

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ code index.htm

347460.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

<li>브랜치</li>

</ul>

</header>

<h1>hello GIT world!</h1>

<footer>

copyright all right 2020 reserved

by jinyphp

</footer>

</body>

</html>

 

두 줄로 만들고, hojinlee를 jinyphp로 수정했습니다. 이어서 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git commit -am "edit copyright"

347490.png
등록 및 커밋

[master c6e2ed7] edit copyright

1 file changed, 2 insertion(+)

두 브랜치에 있는 index.htm 파일에서 동일한 위치의 코드를 각각 수정했습니다.

311312.jpg 그림 8-24 동일한 위치의 코드를 수정한 후 커밋 브랜치

316408.png 

master 브랜치와 footer 브랜치 각각에 커밋이 하나씩 추가되었습니다. 서로 다른 브랜치에서 각각 커밋했기 때문에 그래프가 두 갈래로 갈라집니다. 소스트리에서 갈라진 로그 기록을 확인할 수 있습니다.

311092.jpg 그림 8-25 소스트리에서 분기된 커밋 확인

0825.jpg 

서로 다르게 분기된 브랜치이기 때문에 3-way 병합을 시도하겠습니다. master 브랜치인지 확인한 후 병합 명령어를 실행합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

347521.png
기준 브랜치

$ git merge footer

347551.png
병합 실행

Auto-merging index.htm

CONFLICT (content): Merge conflict in index.htm

Automatic merge failed; fix conflicts and then commit the result.

347587.png
충돌 발생

자동으로 병합하지 않고 충돌이 발생합니다. 충돌이 발생한 것은 두 브랜치의 index.htm 파일에서 같은 위치의 내용을 각각 다르게 수정했기 때문입니다.

 

충돌 해결 방법을 알아봅시다. 지금까지 보지 못한 새로운 메시지가 출력되었습니다. 자동으로 병합하는 과정에서 충돌이 발생되면 깃은 “Merge Conflicts” 메시지를 출력합니다. 소스트리에서 그래프를 확인하면 충돌이 발생하여 커밋되지 않은 변경 사항이 하나 추가되어 있습니다.

311096.jpg 그림 8-26 소스트리에서 충돌 확인

0826.jpg 

여기서 알 수 있는 것은 병합 충돌이 발생하면 자동으로 커밋이 생성되지 않는다는 것입니다. 충돌이 발생하면 깃은 충돌 메시지를 출력하고 병합 작업을 중단합니다.

이렇게 충돌이 발생하면 담당 개발자가 직접 수동으로 해결해야 합니다. 어떤 충돌 상태인지 알아보기 위해 깃 상태를 확인합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master|MERGING)

347778.png
366735.png
347753.png
충돌 사항 표시

$ git status

347620.png
상태 확인

On branch master

You have unmerged paths.

320702.png
충돌 사항

(fix conflicts and run "git commit")

(use "git merge --abort" to abort the merge)

 

Unmerged paths:

(use "git add <file>..." to mark resolution)

both modified: index.htm

no changes added to commit (use "git add" and/or "git commit -a")

충돌 내용이 메시지로 출력됩니다. “Unmerged” 메시지를 확인할 수 있습니다. 깃 배시에도 master|MERGING으로 표시된 것을 확인할 수 있습니다. 현재 충돌된 병합을 해결해야 하는 상태라고 표시합니다.

 

사실 이러한 충돌은 버전 관리 시스템에서는 흔히 발생하는 문제입니다. 실제 사용하다 보면 깃 또한 충돌을 피할 수 없습니다. 하지만 피할 수 없더라도 예방은 가능합니다. 내부적으로 팀원 간 규칙을 정하고 상의하면서 개발을 진행하면 향후 발생할 충돌을 많이 줄일 수 있습니다. 다른 방안으로는 master 브랜치 내용을 자주 자신의 브랜치로 병합하는 것입니다. 자주 커밋하고 병합할수록 충돌이 발생할 기회는 적습니다. 많은 내용을 수정할수록 병합할 때 충돌이 발생하기 쉽습니다. 자신의 브랜치 상태가 최신일수록 향후 병합할 때 발생하는 충돌을 최소화할 수 있습니다.

방금 실행한 병합을 취소할 때는 --abort 옵션을 실행합니다.

infoh@hojin1 MINGW64 /e/gitstudy08 (master|MERGING)

$ git merge --abort

330528.png
병합 명령 취소

infoh@hojin1 MINGW64 /e/gitstudy08 (master)

Note

line.jpg
line.jpg
line.jpg
315352.png
 

8.5.3 수동으로 충돌 해결

병합 충돌이 발생하면 결국 수동으로 해결해야 합니다. 직접 소스 코드를 보고 충돌된 부분을 확인한 후 코드를 수정합니다.

먼저 충돌한 소스 코드를 확인합니다. 깃은 충돌이 발생하면 충돌된 코드 내용을 기호와 함께 표시합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master|MERGING)

$ code index.htm

347682.png
VS Code 실행

311098.jpg 그림 8-27 index.htm 파일의 충돌 사항 표시

0827.jpg 

 

충돌은 두 부분으로 표시됩니다. 하나는 기준이 되는 브랜치 내용이고, 다른 하나는 병합하고자 하는 브랜치 내용입니다.

311314.jpg 그림 8-28 충돌 코드

316494.png 

충돌한 내용을 수정할 때는 깃에서 표시한 충돌 기호도 함께 삭제해야 합니다. 코드를 수정하고 표시된 기호도 같이 삭제하여 다음과 같이 수정한 후 저장합니다.

index.htm

...

<footer>

copyright all right 2018 reserved

by jiny

</footer>

</body>

</html>

 

저수준 명령어 git ls-files -u를 사용하여 충돌한 파일들의 집합을 확인할 수 있습니다.



$ git ls-files -u

Note

line.jpg
line.jpg
line.jpg
315425.png
 

직접 코드를 수정하여 충돌을 해결했습니다. 충돌이 발생하면 병합 커밋을 자동으로 생성하지 않습니다. 충돌을 해결한 후 병합 커밋을 직접 만들어야 합니다. 직접 충돌을 해결하면 파일은 modified 상태가 됩니다. 이를 다시 스테이지 영역에 등록하고 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master|MERGING)

$ git add index.htm

320765.png
스테이지에 등록

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master|MERGING)

$ git commit -m "resolve complicit"

320795.png
병합 커밋 작성

[master 533051d] resolve complicit

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

366790.png
충돌 해결

병합 커밋을 생성하면 깃의 충돌 마크는 자동으로 없어집니다. 깃 배시에서 master|MERGING이 master로 돌아온 것을 확인합니다.

8.5.4 소스트리에서 충돌 해결

소스트리에서도 병합 충돌을 확인할 수 있습니다. 이미 8.5.3절에서 충돌을 해결했기 때문에 8.5.2절까지 진행하여 실습을 위한 충돌을 만든 상황이라고 가정한 채 설명하겠습니다.

충돌이 발생하면 ‘스테이지에 올라간 파일’과 ‘스테이지에 올라가지 않은 파일’ 두 영역에 파일이 표시됩니다. 파일을 클릭하면 충돌 메시지를 확인할 수 있습니다.

311102.jpg 그림 8-29 소스트리에서 충돌 확인

0829.jpg 

소스트리는 병합 커밋을 자동으로 생성할 수 있는 옵션을 제공합니다. 충돌한 파일에서 마우스 오른쪽 버튼을 누릅니다.

311104.jpg 그림 8-30 소스트리에서 충돌 해결

0830.jpg 

충돌 해결 메뉴를 선택하면 다양한 해결 옵션이 보입니다. 이 옵션들을 사용하여 충돌을 간단하게 해결할 수 있습니다. 하지만 가능하면 직접 수동으로 수정하는 것이 안전합니다.

311106.jpg 그림 8-31 병합 커밋 생성

0831.jpg 

충돌을 해결하면 두 브랜치가 하나로 표시됩니다.

311108.jpg 그림 8-32 병합을 완료한 브랜치

0832.jpg 

8.6

307874.png
307921.png
브랜치 병합 여부 확인

git

 

다수의 브랜치가 있을 때는 어느 브랜치가 병합을 완료한 것인지 알기 어렵습니다. 브랜치를 병합한 후에 바로 병합된 브랜치를 삭제한다면 이러한 혼동을 줄일 수 있을 것입니다.

깃은 병합한 브랜치와 병합하지 않은 브랜치를 구분하는 옵션을 제공합니다.

$ git branch --merged

 

master 브랜치에서 이 명령어를 실행해 봅시다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git branch --merged

347859.png
브랜치 목록

feature

footer

* master

병합한 브랜치는 별표(*) 기호로 표시됩니다. 병합을 완료한 브랜치는 앞에서 배운 -d 옵션을 사용하여 삭제할 수 있습니다.

병합하지 않은 브랜치는 --no-merged 옵션으로 확인할 수 있습니다.

$ git branch --no-merged

 

병합하지 않은 브랜치는 -d 옵션으로 삭제되지 않으므로 -D 옵션을 사용합니다.

.

8.7

307956.png
308003.png
리베이스

git

 

브랜치를 합치는 방법은 두 가지입니다. 앞에서 배운 병합(merge)과 이 절에서 학습할 리베이스(rebase)입니다. 이번에는 커밋 순서를 재배열하는 리베이스 병합을 알아보겠습니다.

리베이스는 커밋의 트리 구조를 재배열합니다. 커밋을 재배열하는 변경 결과가 병합과 유사합니다. 사실 실무에서는 merge 명령어보다는 커밋을 재배열하는 리베이스를 더 선호하는 편입니다.

8.7.1 베이스

다시 브랜치 개념을 떠올려 봅시다. 모든 브랜치는 뿌리가 있습니다(master 브랜치는 예외입니다). 브랜치는 특정 커밋을 가리키는 포인터입니다. 그리고 가리키는 특정 커밋은 브랜치가 파생된 기준이 됩니다. 즉, 브랜치는 커밋 하나를 기준으로 새로운 작업을 진행할 수 있는 분리된 작업 경로를 의미합니다.

311316.jpg 그림 8-33 브랜치의 기준 커밋

316626.png 

그림에서 새로운 브랜치가 커밋2에서 파생됩니다. 새로운 브랜치가 파생되는 커밋2를 베이스(base)라고 합니다. 병합에서는 이를 공통 조상 커밋이라고 합니다.

8.7.2 베이스 변경

리베이스(rebase)는 베이스 앞에 ‘다시’를 의미하는 re가 붙은 단어입니다. 파생된 브랜치의 기준이 되는 베이스 커밋을 변경하는 것입니다.

그럼 브랜치의 베이스는 왜 변경할까요? 커밋의 진행 모습을 단순화하기 위해서입니다. 브랜치가 많아지면 커밋을 관리하고 파악하기 어렵습니다. 마치 꼬여 있는 기찻길처럼 단계별로 커밋을 따라가면서 코드를 확인해야 합니다. 복잡한 브랜치의 수많은 경로는 코드의 진행 상황을 한눈에 파악하기 어렵게 합니다.

리베이스는 코드의 베이스 분기점을 변경하여 마치 하나의 기찻길처럼 만듭니다. 여러 갈래로 갈라지지 않아 커밋의 진행 사항을 좀 더 쉽게 파악할 수 있습니다.

311318.jpg 그림 8-34 베이스 이동

316628.png 

그림처럼 리베이스는 브랜치 A의 공통된 조상인 커밋2를 master 브랜치의 마지막 커밋6으로 변경합니다. 그리고 모든 브랜치의 커밋들을 리베이스된 커밋6 이후로 재정렬합니다.

8.7.3 리베이스 vs 병합

병합은 파생된 두 브랜치를 하나로 합치는 과정입니다. 병합하려면 두 브랜치의 공통 조상 커밋을 먼저 찾아야 합니다. 공통 조상 커밋을 찾으면 서로 다르게 커밋이 진행된 두 브랜치를 3-way 방식으로 병합할 수 있습니다. 공통 조상 커밋은 두 브랜치를 병합하는 베이스 커밋입니다. 병합하는 두 브랜치는 순차적으로 커밋을 비교하면서 마지막 최종 커밋을 생성합니다.

311320.jpg 그림 8-35 3-way 병합

316630.png 

반면에 리베이스는 두 브랜치를 서로 비교하지 않고 순차적으로 커밋 병합을 시도합니다. 리베이스에서 브랜치의 커밋을 결합하는 순서를 살펴봅시다.

리베이스를 하면 먼저 공통 조상 커밋을 찾습니다. 리베이스는 베이스 커밋을 변경하여 두 브랜치의 커밋 위치를 바꿉니다. 그리고 파생된 브랜치의 diff를 임시 공간에 잠시 보관합니다. master 브랜치의 커밋1 → 커밋2 → 커밋5 → 커밋6까지 진행합니다. 기존 베이스 커밋2에서 커밋6으로 베이스 기준점을 변경합니다. 변경하는 기준 브랜치의 마지막 커밋에서 차례로 임시 공간에 저장한 diff를 하나씩 적용합니다. 새로운 베이스 기준점을 기반으로 한 브랜치에서 커밋3 → 커밋4를 커밋6에서 연장하여 수정 재배치합니다.

311322.jpg 그림 8-36 커밋 재배치

316666.png 

결과적으로 브랜치의 커밋4는 최종 코드로 모든 코드 내용이 반영되어 있습니다. 커밋4 입장에서는 두 브랜치를 병합한 결과물입니다.

리베이스 결과물을 보면 기존 병합과 두 가지 차이점이 있습니다. 첫째, 3-way 병합은 병합 커밋이 있지만, 리베이스를 하면 병합 커밋은 없습니다. 둘째, 브랜치의 마지막을 가리키는 커밋 위치가 다릅니다. 브랜치 A는 커밋4를 가리키지만, master 브랜치는 아직 커밋6을 가리킵니다.

8.7.4 리베이스 명령어

리베이스 작업은 rebase 명령어를 사용합니다. 또는 다른 명령어의 옵션으로 리베이스 기능을 실행할 수 있습니다.

$ git rebase 브랜치

 

실습을 위해 index.htm 파일을 수정하고 커밋하겠습니다. 먼저 리베이스 실습을 위한 새로운 description 브랜치를 생성합니다.

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git checkout -b description

347900.png
브랜치 생성

그리고 description 브랜치에서 index.htm 파일을 수정하고 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (description)

$ code index.htm

347930.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

<li>브랜치</li>

</ul>

</header>

<h1>hello GIT world!</h1>

<h2>깃은 소스의 변경 이력을 관리할 수 있습니다.</h2>

<footer>

copyright all right 2020 reserved

by jiny

</footer>

</body>

</html>

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (description)

$ git commit -am "add description"

347960.png
등록 및 커밋

[description 079bdc1] add description

1 file changed, 1 insertion(+)

다시 master 브랜치로 체크아웃합니다. master 브랜치에서도 index.htm을 수정한 후 두 번 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (description)

$ git checkout master

347990.png
브랜치 이동

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ code index.htm

348020.png
VS Code 실행

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

<li>브랜치</li>

<li>병합</li>

</ul>

</header>

<h1>hello GIT world!</h1>

<footer>

copyright all right 2020 reserved

by jiny

</footer>

</body>

</html>

 

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git commit -am "add menu5"

348050.png
등록 및 커밋

[master 8959f0c] add menu5

1 file changed, 1 insertion(+)

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ code index.htm

348088.png
VS Code 실행

 

index.htm

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Page Title</title>

</head>

<body>

<header>

<ul>

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

<li>브랜치</li>

<li>병합</li>

<li>리베이스</li>

</ul>

</header>

<h1>hello GIT world!</h1>

<footer>

copyright all right 2020 reserved

by jiny

</footer>

</body>

</html>

 

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git commit -am "add menu6"

348119.png
등록 및 커밋

[master a7fe40b] add menu6

1 file changed, 1 insertion(+)

베이스 커밋 하나를 기준으로 서로 다른 브랜치에 각각의 커밋이 추가되었습니다. 소스트리에서 그래프를 확인하면 다음과 같이 표시됩니다.

311110.jpg 그림 8-37 소스트리에서 브랜치 확인

0836.jpg 

보통 브랜치별로 각각 커밋이 진행된 경우에는 3-way 병합을 합니다. 하지만 이번에는 리베이스를 이용하여 두 브랜치를 병합해 보겠습니다.

8.7.5 리베이스 병합

리베이스는 병합 기준 브랜치가 merge 명령어와 반대입니다. merge 명령어를 사용한 병합은 현재의 기준 브랜치에서 다른 브랜치를 읽어 와서 결합합니다.

311326.jpg 그림 8-38 merge 명령어를 사용한 병합

316688.png 

하지만 리베이스는 병합되는 브랜치 방향이 반대입니다.

311328.jpg 그림 8-39 리베이스 병합

316690.png 

대부분 처음에는 이러한 병합 기준을 종종 혼동하곤 합니다.

지금까지 실습 과정을 그림으로 나타내면 다음과 같습니다.

311331.jpg 그림 8-40 description 브랜치의 작업 내역

316726.png 

리베이스를 할 수 있게 description 브랜치로 체크아웃하겠습니다.

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git checkout description

320825.png
리베이스 브랜치

Switched to branch 'description'

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (description)

description 브랜치에서 원본 master 브랜치를 리베이스합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (description)

$ git rebase master

320856.png
master 브랜치를 리베이스

First, rewinding head to replay your work on top of it...

Applying: add description

리베이스 명령이 실행되면 파생 브랜치의 커밋들은 기준 브랜치의 마지막 커밋으로 재정렬됩니다. 소스트리에서 결과를 확인해 봅시다.

311112.jpg 그림 8-41 리베이스 결과

0840.jpg 

master 브랜치의 마지막 커밋 ‘add menu6’ 뒤에 파생 브랜치의 커밋이 연결된 것을 볼 수 있습니다. 두 브랜치를 하나의 그래프 모양으로 합친 형태입니다.

8.7.6 리베이스되었는지 확인

리베이스는 베이스 커밋을 변경하여 병합한다고 했습니다. 베이스 커밋을 변경하는 과정에서 커밋들은 재배치 작업을 합니다. 이 과정에서 커밋의 해시 값이 변경됩니다.

리베이스한 후 로그를 확인해 봅시다. 커밋의 해시 값을 주의 깊게 살펴보세요.

infoh@DESKTOP MINGW64 /e/gitstudy08 (description)

$ git log -3

348153.png
로그 확인

commit 48caea016f0e330cfc1dfcd587996fa9a32042fd (HEAD -> description)

Author: hojin <infohojin@gmail.com>

Date: Sat May 18 17:27:09 2019 +0900

add description

 

commit a7fe40bb622f6c8af0b1f25b0d86ea96c7896c50 (master)

Author: hojin <infohojin@gmail.com>

Date: Sat May 18 17:28:59 2019 +0900

add menu6

 

commit 8959f0cca024504cfe321adf440c9c888f8e4693

Author: hojin <infohojin@gmail.com>

Date: Sat May 18 17:28:29 2019 +0900

add menu5

로그를 확인하니 변경된 곳이 있습니다. 리베이스 병합 이후에 커밋 ID를 변경했군요.

311338.jpg 그림 8-42 커밋 해시 값 변경

316740.png 

리베이스는 커밋 위치를 변경합니다. 따라서 커밋 위치가 변경될 때 해시 값 중복을 방지하려고 새로운 커밋 해시를 생성합니다.

8.7.7 리베이스 후 브랜치

소스트리에서 리베이스를 완료한 후 브랜치를 다시 살펴봅시다. 리베이스 병합 이후 커밋은 정리되었지만, 브랜치 모양이 약간 다릅니다.

311114.jpg 그림 8-43 리베이스 후 브랜치의 마지막 커밋 위치

0842.jpg 

일반적으로 병합을 한 후 두 브랜치는 같은 커밋 ID를 가리킵니다. 하지만 소스트리에서 확인된 브랜치 위치는 서로 다릅니다.

 

311340.jpg 그림 8-44 브랜치의 HEAD 포인터

316787.png 

리베이스는 커밋 위치를 재조정할 뿐 브랜치의 HEAD 포인터까지 옮겨 주지는 않습니다. 리베이스한 후에는 이러한 병합 브랜치의 HEAD를 맞추어야 합니다. 즉, 리베이스된 브랜치를 병합해야 합니다.

병합을 위해 master 브랜치로 체크아웃합니다. 그리고 master 브랜치에서 merge 명령어를 실행합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (description)

$ git checkout master

348186.png
브랜치 이동

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git merge description

320887.png
HEAD 포인터 조정(병합)

Updating a7fe40b..48caea0

Fast-forward

348218.png
병합 방식 확인

index.htm | 1 +

1 file changed, 1 insertion(+)

병합한 후 소스트리에서 브랜치 상태를 다시 확인해 보세요.

311117.jpg 그림 8-45 소스트리에서 HEAD 포인터 조정 확인

0844.jpg 

두 브랜치 HEAD가 동일한 커밋 위치를 가리키고 있습니다.

리베이스한 후에 실행한 병합 메시지도 살펴볼까요? Fast-Forward 방식으로 병합했다는 것을 알 수 있습니다. HEAD 포인터의 위치만 생각해 보면 master 브랜치는 추가 커밋이 없는 상태입니다. 그리고 리베이스한 브랜치에만 커밋이 진행된 것처럼 보입니다. 즉, 리베이스한 후 HEAD 포인터의 위치 모양은 Fast-Forward 병합을 실습할 때와 같은 형태입니다.

리베이스는 커밋을 재배치만 할 뿐 실제 병합과 같은 최종 상태는 가지지 않습니다. 즉, 리베이스한 후에도 HEAD 포인터를 일치하기 위해 Fast-Forward 병합을 실행해 주어야 합니다. 두 브랜치의 HEAD를 일치시키는 작업까지 해야 최종 병합을 완성할 수 있습니다.

리베이스 및 병합 작업까지 했다면 필요 없는 브랜치는 삭제합시다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git branch -d description

Deleted branch description (was 48caea0).

이처럼 리베이스하게 되면 복잡한 트리 모양의 구조가 아니라 선형 구조로 브랜치를 변경할 수 있습니다.

8.7.8 리베이스 충돌과 해결

리베이스는 기준점을 변경합니다. 리베이스 역시 병합 과정에서 충돌이 발생할 수 있습니다. 리베이스 충돌 또한 사용자가 직접 수동으로 해결해야 합니다.

실습을 위해 리베이스 충돌 환경을 만들어 보겠습니다. 먼저 새로운 menu 브랜치를 생성한 후 체크아웃합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git checkout -b menu

348248.png
브랜치 생성

index.htm에서 코드 메뉴를 일부 변경하고 두 번 커밋하겠습니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)

$ code index.htm

348282.png
VS Code 실행

index.htm

...

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

<li>브랜치</li>

<li><ul>병합</ul></li>

<li>리베이스</li>

...

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)

$ git commit -am "edit menu5"

348312.png
등록 및 커밋

[menu 8381da6] edit menu5

1 file changed, 1 insertion(+), 1 deletion(-)

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)

$ code index.htm

348345.png
VS Code 실행

index.htm

...

<ul>

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

<li>브랜치</li>

<li>병합

<ul><li>리베이스</li></ul>

</li>

</ul>

...

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)

$ git commit -am "edit menu6"

348376.png
등록 및 커밋

[menu 9f0bc0d] edit menu6

1 file changed, 5 insertions(+), 2 deletions(-)

master 브랜치에서도 동일한 위치의 내용을 수정하여 충돌을 만들겠습니다. master 브랜치로 체크아웃합니다. 그리고 master 브랜치에서 index.htm 파일을 수정하고 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)

$ git checkout master

348406.png
브랜치 이동

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ code index.htm

348437.png
VS Code 실행

 

index.htm

...

<ul>

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

<li>브랜치</li>

<li>병합<ul></ul></li>

<li>리베이스</li>

</ul>

...

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git commit -am "edit submenu for menu5"

348467.png
등록 및 커밋

[master 93aa6eb] edit submenu for menu5

1 file changed, 1 insertion(+), 1 deletion(-)

변경된 상태를 소스트리에서 확인해 보세요.

311121.jpg 그림 8-46 소스트리에서 menu 브랜치 작업 확인

0845.jpg 

서로 다른 브랜치 모양으로 분기되었습니다. 리베이스를 사용해서 병합해 봅시다. menu 브랜치로 체크아웃합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git checkout menu

320917.png
리베이스 브랜치

Switched to branch 'menu'

이제 리베이스 명령을 실행합니다. 두 브랜치는 충돌이 발생합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)

$ git rebase master

First, rewinding head to replay your work on top of it...

Applying: edit menu5

Using index info to reconstruct a base tree...

M index.htm

Falling back to patching base and 3-way merge...

Auto-merging index.htm

CONFLICT (content): Merge conflict in index.htm

348506.png
충돌

error: Failed to merge in the changes.

hint: Use 'git am --show-current-patch' to see the failed patch

Patch failed at 0001 edit menu5

 

Resolve all conflicts manually, mark them as resolved with

"git add/rm <conflicted_files>", then run "git rebase --continue".

You can instead skip this commit: run "git rebase --skip".

To abort and get back to the state before "git rebase", run "git rebase --abort".

두 브랜치가 충돌했다는 메시지가 출력되었습니다. 충돌이 발생하면 문제를 직접 해결해야 합니다. 코드를 확인해 볼까요?

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu|REBASE 1/2)

366840.png
충돌 표시

$ code index.htm

348536.png
VS Code 실행

311125.jpg 그림 8-47 충돌한 파일 내용

0846.jpg 

앞에서 배운 병합과 동일하게 충돌 기호가 표시됩니다. 다음과 같이 직접 수정합시다.

index.htm

...

<ul>

<li>깃소개</li>

<li>깃설치</li>

<li>커밋</li>

<li>브랜치</li>

<li>병합

<ul><li>리베이스</li>

</ul>

</li>

</ul>

...

 

리베이스는 커밋을 하나씩 따라가면서 위치를 재조정합니다. 충돌을 수정한 후에는 rebase 명령어와 --continue 옵션을 사용합니다.

$ git rebase --continue

 

수정한 파일을 다시 스테이지 상태로 변경합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu|REBASE 1/2)

$ git add index.htm

348605.png
등록

리베이스를 이용하여 병합할 때는 충돌된 부분들을 한 단계씩 해결해 나가면서 병합할 수 있습니다. --continue 옵션을 사용하여 병합을 더 진행합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu|REBASE 1/2)

$ git rebase --continue

348635.png
계속 진행

Applying: edit menu5

Applying: edit menu6

Using index info to reconstruct a base tree...

M index.htm

Falling back to patching base and 3-way merge...

No changes -- Patch already applied.

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)

348665.png
충돌 해결

모든 충돌을 해결하면 리베이스 작업이 종료됩니다.2

--skip 옵션을 사용하여 특정 커밋의 충돌을 제외할 수 있습니다. 하지만 추천하는 방법은 아닙니다. 대부분 코드는 이전 코드와 많이 연결되어 있기 때문에 직접 문제를 해결하고 --continue 옵션을 사용하여 다음 단계로 넘어가는 것이 좋습니다.

리베이스를 취소하고 싶다면 --abort 옵션을 사용합니다.

$ git rebase --abort

Note

line.jpg
line.jpg
line.jpg
315498.png
 

리베이스 충돌을 해결했다면 이제 브랜치를 정리할 차례입니다. master 브랜치로 체크아웃한 후 menu 브랜치를 병합합니다. 그리고 병합된 menu 브랜치는 삭제합니다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (menu)

$ git checkout master

348699.png
브랜치 이동

Switched to branch 'master'

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git merge menu

348730.png
병합, HEAD 일치

Updating 93aa6eb..690cc95

Fast-forward

index.htm | 7 +++++--

1 file changed, 5 insertions(+), 2 deletions(-)

 

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git branch -d menu

348760.png
브랜치 삭제

Deleted branch menu (was 690cc95).

8.7.9 rebase 명령어로 커밋 수정

마지막 커밋은 --amend 옵션으로 수정할 수 있습니다. 이 방법 외에 rebase 명령어로도 최종 커밋을 수정할 수 있습니다.

실제 병합은 아니지만 리베이스는 커밋 위치를 재조정하여 병합과 유사한 효과를 보입니다. 그리고 Fast-Forward 병합을 이용하여 선형 구조 형태로 브랜치 모양을 정리하죠. 리베이스는 커밋을 재조정하는 것 외에도 여러 커밋을 한 커밋으로 묶을 수 있습니다. 이때는 -i 옵션을 사용합니다.

실습하기 전에 현재 저장소 상태를 확인합시다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git log -3

348795.png
로그 확인

commit 690cc959dd410aad516c17c3bd1b46e3e022b2b6 (HEAD -> master)

Author: hojin <infohojin@gmail.com>

Date: Sat May 18 18:08:28 2019 +0900

edit menu5

 

commit 93aa6eb8ad3cf50845dd04d9b4e92838279df2b4

Author: hojin <infohojin@gmail.com>

Date: Sat May 18 18:12:56 2019 +0900

edit submenu for menu5

 

commit 48caea016f0e330cfc1dfcd587996fa9a32042fd

Author: hojin <infohojin@gmail.com>

Date: Sat May 18 17:27:09 2019 +0900

add description

우리는 세 번 커밋해서 리베이스했습니다. 하지만 이 커밋들은 작업이 비슷합니다. 이 커밋들을 커밋 하나로 묶어 봅시다.

infoh@DESKTOP MINGW64 /e/gitstudy08 (master)

$ git rebase -i HEAD~3

348827.png
커밋 묶기

명령어를 입력하면 메시지를 입력할 수 있는 vi 에디터가 실행됩니다. 리베이스 병합할 커밋들의 정보도 자동으로 작성됩니다.

311127.jpg 그림 8-48 메시지를 입력할 수 있는 vi 에디터

0847.jpg
pick 48caea0 add description

pick 93aa6eb edit submenu for menu5

pick 690cc95 edit menu5

 

# Rebase a7fe40b..690cc95 onto a7fe40b (3 commands)

#

# Commands:

# p, pick <commit> = use commit

# r, reword <commit> = use commit, but edit the commit message

# e, edit <commit> = use commit, but stop for amending

# s, squash <commit> = use commit, but meld into previous commit

# f, fixup <commit> = like "squash", but discard this commit's log message

# x, exec <command> = run command (the rest of the line) using shell

# d, drop <commit> = remove commit

# l, label <label> = label current HEAD with a name

# t, reset <label> = reset HEAD to a label

# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]

# . create a merge commit using the original merge commit's

# . message (or the oneline, if no original merge commit was

# . specified). Use -c <commit> to reword the commit message.

#

# These lines can be re-ordered; they are executed from top to bottom.

#

# If you remove a line here THAT COMMIT WILL BE LOST.

 

리베이스 메시지를 저장하면 다음 메시지를 출력한 후 커밋 3개가 커밋 하나로 변경됩니다.

Successfully rebased and updated refs/heads/master.

이처럼 리베이스는 여러 커밋을 커밋 하나로 합칠 수 있습니다. 이때 합친 커밋에는 새 해시 값이 부여됩니다.

8.7.10 리베이스할 때 주의할 점

리베이스는 커밋 위치와 해시 값을 변경합니다. 저장소를 외부에 공개했다면 공개된 순간부터 커밋은 리베이스를 사용하지 않는 것이 원칙입니다.

리베이스는 외부로 코드를 푸시하거나 공개하기 전에 로컬에서만 실행하는 것이 좋습니다. 외부에 공개된 커밋을 리베이스하면 커밋 위치와 해시 값이 변경되어 너무 혼란스럽습니다. 공개된 커밋을 변경할 때는 다음 장에서 배울 revert 명령어를 사용합니다.

8.8

308048.png
308095.png
정리

git

 

다수의 개발자와 협업할 때 병합과 충돌은 매우 자주 발생합니다. 충돌을 해결하고 병합을 처리하는 것은 쉬운 작업이 아닙니다. 개발 과정에서 병합 충돌을 최소화하고 예방하려면, master 브랜치 내용을 자주 반영하여 병합하는 것이 좋습니다.

원격 저장소의 master 브랜치를 모니터링하고, 변화된 부분을 즉시 반영하면서 작업하면 충돌을 최소화하거나 예방할 수 있습니다.

1 브랜치 삭제 방법은 회사마다 운영 정책에 따라 조금씩 다릅니다.

2 git rebase --continue 명령어를 실행했는데 완벽히 리베이스되지 않았다면, git add 명령어를 한 번 더 실행한 후 git rebase --continue 명령어를 실행해 보세요.

