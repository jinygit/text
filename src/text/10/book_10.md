10장

배포 관리와 태그

이 장에서는 완성된 코드의 관리와 배포 방법을 알아보겠습니다. 깃은 코드를 안정된 상태로 유지하며 완성된 코드를 사용자에게 배포합니다.

10.1 배포

10.2 버전

10.3 태그

10.4 태그 목록

10.5 Annotated 태그

10.6 Lightweight 태그

10.7 특정 커밋 태그

10.8 태그를 사용한 체크아웃

10.9 태그 공유

10.10 정리

 

QUICK GUIDE

태그 생성

331308.png
태그 전송

331337.png
10.1

308485.png
308532.png
배포

git

 

프로그램을 개발한 후에는 완성된 결과물을 최종 사용자에게 전달해야 합니다. 이때 최종 사용자에게 전달하는 과정을 배포라고 합니다.

개발을 완료했다고 해서 결과물을 직접 사용자에게 배포할 수 없습니다. 완성된 형태로 결과물을 배포하려면 코드를 정리하는 작업들이 추가로 필요합니다. 개발 단계에서 발생한 테스트 메시지나 불필요한 주석들을 정리합니다. 이러한 정리 작업을 거쳐 코드를 좀 더 깔끔하게 만들 수 있고, 배포도 가능합니다. 더불어 정리 작업은 조금이지만 코드 용량을 줄이는 효과도 있습니다. 즉, 배포는 정리된 최종 결과물을 만드는 과정입니다.

과거에는 최종 결과물인 소프트웨어를 CD나 USB 등에 담아 고객에게 전달했습니다. 하드웨어 같은 장비들은 ROM이라는 저장 장치에 저장해서 배포했습니다. 요즘에는 인터넷이 발달하면서 과거의 물리적인 배포 대신 온라인으로 배포합니다. 인터넷이 연결된 서버에서 최종 결과물의 파일을 직접 내려받을 수 있습니다. 온라인 배포는 물리적 생산 비용과 유통 비용이 들지 않고, 빠르게 배포할 수 있습니다. 이렇게 배포 프로세스가 빨라지면서 코드를 안정적으로 유지하고 테스트하는 것이 더 중요해졌습니다.

따라서 개발자는 코드를 안정적인 상태로 유지하면서 쉽게 배포할 수 있는 도구들이 필요해졌습니다. 배포를 잘하려면 코드를 깔끔하게 정리할 수 있는 환경이 필요합니다. 또 사용자가 파일을 쉽게 내려받을 수 있게 해야 합니다. 이러한 이유로 깃은 코드를 배포하는 데도 많이 사용합니다.

10.2

308604.png
308651.png
버전

git

 

세상에 완벽한 것은 없습니다. 코드도 마찬가지입니다. 배포 당시에는 발견하지 못했는데, 이후에 잘못된 동작을 하거나 예외적인 상황이 생겨 처리하지 못하는 동작들이 있을 수 있습니다. 또는 최종 사용자가 추가 기능을 요구할 때도 있습니다. 이때는 코드를 수정해야 합니다. 즉, 코드는 개발을 완료한 후에도 계속 수정됩니다.

코드를 수정했다면 개발자 또는 최종 사용자가 이를 확인하고 구별할 수 있어야 합니다. 코드에서 이러한 차이를 구별할 수 있게 하는 것이 바로 버전(version)입니다. 버전은 프로그램을 수정하거나 개선할 때마다 코드를 구분하려고 부여된 식별자를 의미하며, 보통 숫자를 사용합니다. 숫자가 클수록 최근에 수정된 코드입니다. 버전업(version up)은 오래된 버전의 프로그램을 최신 버전의 코드로 변경하는 것을 의미합니다.

버전 번호를 부여할 때는 약간의 규칙이 있습니다. 이 규칙은 오래 전부터 업계에서 사용하던 형태로 꼭 사용할 필요는 없지만, 가능하면 따르는 것을 권장합니다.

기본적인 버전은 단일 번호 하나로 구성되어 있습니다. 단일 번호는 프로그램에서 큰 기능을 변경했을 때 바뀝니다. 첫 자리가 0으로 시작하면 아직 초기 개발 중인 제품이라는 의미입니다. 정식 버전은 1부터 시작합니다. 이를 메이저(major) 버전이라고 합니다. 메이저 번호를 변경하면 하위 버전과 호환성이 낮아질 수도 있습니다.

메이저 버전 다음으로 작은 코드의 변화는 점(.)을 사용하여 구분합니다. 보통 두 자리 또는 세 자리 형태의 숫자로 작성합니다.

● 두 자리: 1.0
● 세 자리: 2.1.4
보통 두 번째 자리는 메이저 버전에서 기능을 추가하거나 변경 사항이 있을 때 바꿉니다. 다른 말로 마이너(minor) 번호라고도 합니다. 세 번째 자리는 버그 수정 등 미미한 변화가 있을 때 바꿉니다. 다른 말로 패치(patch) 버전이라고 합니다. 이처럼 세 자리 숫자 형태로 표기하는 버전을 SemVer(Semantic Versioning) 방식이라고 합니다.

버전 용어

•RC(Release Candidate): Candidate는 후보자, 지원자, 가능성 있는 사람이라는 뜻입니다. 즉, 정식 버전이 아닌 베타 버전을 의미합니다. 리눅스 배포판에서 RC 표시를 확인할 수 있습니다. RC는 안정적인 동작을 보장하지 않는 임시 제품이라고 보면 됩니다.

•GA(General Availability): 테스트가 완료된 정식 릴리스 버전을 의미합니다. 안정된 버전입니다.

•M(Milestone): 테스트 버전을 의미합니다. 기능들을 구현할 때마다 테스트하여 피드백을 받는 버전을 의미합니다.

Note

line.jpg
line.jpg
line.jpg
315720.png
 

10.3

308700.png
308747.png
태그

git

 

깃에서는 코드 배포를 관리하려고 태그(tag) 기능을 제공합니다. 커밋은 코드 변화를 기록한 것입니다. 그리고 각 커밋은 서로 다른 코드의 상태를 가집니다. 물론 배포를 위해 최종 정리된 커밋도 있습니다. 깃은 정리된 커밋을 배포할 수 있도록 특수한 포인터를 제공하며, 특정 커밋을 가리키는 포인터로 버전을 관리합니다. 그리고 이 포인터를 태그라고 합니다. 즉, 태그는 특정 커밋의 해시 값을 가리키는 꼬리표를 의미합니다.

최종 사용자는 개발자가 부여한 태그를 사용하여 코드 버전을 구별합니다. 또 태그 포인터로 최종 배포판의 커밋을 구별합니다. 태그는 커밋 해시 값을 기준으로 생성됩니다. 그리고 특정 커밋 해시 값을 가리키는 것뿐만 아니라, 꼬리표 이름과 정보도 포함합니다. 이러한 태그는 추가 정보를 보유하는지 여부에 따라 두 가지로 구분합니다.

● Annotated: 태그 이름 + 정보 포함
● Lightweight: 태그 이름만 포함
이 두 가지 태그의 생성 방법과 활용법은 뒤에서 실습과 함께 알아보겠습니다.

10.4

308781.png
308829.png
태그 목록

git

 

태그 기능을 본격적으로 학습하기에 앞서 간단히 태그 명령어를 알아봅시다. 태그를 사용하려면 tag 명령어를 사용합니다. 단독으로 실행할 수도 있고, 옵션을 추가할 수도 있습니다.

$ git tag

 

 

옵션은 -l 또는 --list 옵션을 같이 사용합니다.



$ git tag -l

소스트리에서는 생성된 태그 목록을 좀 더 쉽게 확인할 수 있습니다. 화면 왼쪽에 태그 탭을 표시하는데, 태그 탭을 선택해서 확장하면 생성된 모든 태그 목록을 확인할 수 있습니다.

331706.jpg 그림 10-1 태그 목록

1001.jpg 

Note

line.jpg
line.jpg
line.jpg
315794.png
 

태그를 실습하기 위해 독립된 실습 환경을 만들겠습니다.

$ cd 실습폴더

$ mkdir gitstudy10

321470.png
새 폴더 만들기

$ cd gitstudy10

 

infoh@DESKTOP MINGW64 /e/gitstudy10

$ git init

321501.png
깃 초기화

Initialized empty Git repository in E:/gitstudy10/.git/

version.htm 파일을 생성하고 코드를 입력한 후 저장합니다. 그리고 첫 번째 커밋을 합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ code version.htm

350288.png
VS Code 실행

version.htm

<h1>태그 버전 실습 파일입니다.</h1>

 

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git add version.htm

350318.png
등록


 

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git commit -m "first"

350349.png
커밋

[master (root-commit) 3c92e35] first

1 file changed, 1 insertion(+)

create mode 100644 version.htm

실습 저장소가 준비되었습니다. 이제 파일에 코드를 하나씩 추가하면서 태그를 알아보겠습니다.

10.5

308871.png
308918.png
Annotated 태그

git

 

Annotated 태그는 깃에서 가장 일반적으로 사용하는 태그 방법입니다. Annotated는 ‘주석이 달린’이라는 뜻입니다.

10.5.1 태그 생성

Annotated 태그를 생성할 때는 커밋의 해시 값뿐 아니라 추가로 생성자 정보를 같이 넣을 수 있습니다. 예를 들어 이메일, 날짜, 메시지 등 정보입니다. 또 GPG 방식으로 서명도 가능합니다.

Annotated 태그를 생성하려면 tag 명령어 뒤에 -a 옵션을 사용합니다.

$ git tag -a 버전

 

 

바로 실습해 보겠습니다. version.htm 파일을 수정하고 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ code version.htm

350380.png
VS Code 실행

version.htm

<h1>태그 버전 실습 파일입니다.</h1>

<ul>

<li>버전 1.0.0 실습</li>

</ul>

 

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git commit -am "test 1.0.0"

350410.png
등록 및 커밋

[master 53028dc] test 1.0.0

1 file changed, 4 insertions(+), 1 deletion(-)

작성한 커밋에 Annotated 태그를 붙이겠습니다.

 

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag -a 1.0.0

321531.png
태그 추가

Annotated 태그를 생성할 때는 태그 메시지를 작성할 수 있는 vi 에디터가 함께 실행됩니다.

311177.jpg 그림 10-2 태그 메시지 작성

1002.jpg
#

# Write a message for tag:

# 1.0.0

# Lines starting with '#' will be ignored.

 

간략한 메시지를 작성하고 저장하면, 정상적으로 태그가 생성됩니다. 태그는 현재의 마지막 커밋을 기준으로 생성되며, 이 커밋은 HEAD 포인터와 일치합니다.

311373.jpg 그림 10-3 태그 생성 위치

317291.png 

앞에서 생성한 태그를 확인해 봅시다. 생성한 태그의 버전을 출력합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag

350440.png
태그 목록

1.0.0

321562.png
태그 확인

이번에는 생성된 태그를 좀 더 자세히 알아봅시다. 로그 기록을 확인합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git log --decorate

350478.png
로그 확인

commit 53028dc1486b42d23253ffd4001a758cef455372 (HEAD -> master, tag: 1.0.0)

321592.png
태그 확인

Author: hojin <infohojin@gmail.com>

Date: Thu May 23 18:07:18 2019 +0900

test 1.0.0

 

commit 3c92e359a0039a5884fec9bb9e0535bdcd188cc4

Author: hojin <infohojin@gmail.com>

Date: Thu May 23 17:37:53 2019 +0900

first

생성된 태그가 53028d 커밋에 1.0.0으로 추가된 것을 확인할 수 있습니다. 커밋에 꼬리표처럼 연결되어 있습니다.

10.5.2 간단한 메시지

Annotated 태그를 생성할 때는 메시지를 작성해야 합니다. 작성할 태그 정보가 간단하다면 vi 에디터를 사용하지 않고, -m 옵션으로 대체할 수 있습니다. 커밋 명령어의 -m 옵션과 유사합니다.

이어서 실습해 보겠습니다. version.htm 파일에 한 줄을 더 추가하고 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ code version.htm

350508.png
VS Code 실행

version.htm

<h1>태그 버전 실습 파일입니다.</h1>

<ul>

<li>버전 1.0.0 실습</li>

<li>버전 1.1.0 실습</li>

</ul>

 

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git commit -am "test 1.1.0"

350539.png
등록 및 커밋

[master da8d211] test 1.1.0

1 file changed, 1 insertion(+)

 

추가된 커밋에 새로운 태그를 만듭시다. 이번에는 간략한 태그 메시지를 작성하려고 -m 옵션을 같이 사용합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag -a 1.1.0 -m "simple tag 1.1.0"

350573.png
태그 생성

정상적으로 태그가 생성되었는지 목록을 확인합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag

350603.png
태그 목록

1.0.0

1.1.0

태그 목록이 2개 출력됩니다. 정상적으로 태그가 추가되었네요.

311377.jpg 그림 10-4 두 번째 태그

317296.png 

10.5.3 소스트리에서 태그 생성

소스트리에서도 태그를 작성할 수 있습니다. 실습을 위해 version.htm 파일을 수정하고 저장한 후 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ code version.htm

350633.png
VS Code 실행

version.htm

<h1>태그 버전 실습 파일입니다.</h1>

<ul>

<li>버전 1.0.0 실습</li>

<li>버전 1.1.0 실습

 

<ul>

<li>수정 작업 1.1.1</li>

</ul>

</li>

</ul>

 

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git commit -am "test 1.1.1"

350663.png
등록 및 커밋

[master f2691a0] test 1.1.1

1 file changed, 5 insertions(+), 1 deletion(-)

소스트리와 gitstudy10 폴더를 연결합시다. 소스트리의 새 탭에서 Add 버튼을 클릭합니다. 탐색을 눌러 앞에서 만든 gitstudy10 폴더를 찾아 선택한 후 추가를 누릅니다. 소스트리와 연결했다면 소스트리에서 로컬 저장소를 확인합니다. 왼쪽의 태그 탭에서 지금까지 생성된 전체 태그를 확인할 수 있습니다.

311179.jpg 그림 10-5 소스트리에서 저장소 태그 확인

1005.jpg 

새롭게 추가한 커밋을 선택합니다. 이 커밋의 메시지는 ‘test 1.1.1’입니다. 이 메시지 위에서 마우스 오른쪽 버튼을 눌러 태그 메뉴를 확인합니다. 또는 소스트리 위쪽에서 태그 10-a.jpg 버튼을 클릭해도 됩니다.

 

311181.jpg 그림 10-6 태그 생성 메뉴

1006.jpg
331928.png
 

태그 창이 열리면 태그 이름을 입력합니다. 책에서는 1.1.1을 입력하겠습니다. 이름을 입력한 후 태그 추가를 누릅니다.

311183.jpg 그림 10-7 태그 이름 입력

1007.jpg
337309.png
337310.png
 

소스트리 그래프에 1.1.1 태그가 생성된 것을 확인할 수 있습니다.

311185.jpg 그림 10-8 태그 생성

1008.jpg
331944.png
 

10.5.4 태그는 중복해서 생성할 수 없다

깃에 등록된 태그 이름은 유일해야 합니다. 즉, 태그는 같은 이름으로 중복해서 생성할 수 없습니다. 실습으로 확인해 봅시다.

version.htm 파일을 수정하고 저장한 후 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ code version.htm

350700.png
VS Code 실행

version.htm

<h1>태그 버전 실습 파일입니다.</h1>

<ul>

<li>버전 1.0.0 실습</li>

<li>버전 1.1.0 실습

<ul>

<li>수정 작업 1.1.1</li>

<li>수정 작업 1.1.2</li>

</ul>

</li>

</ul>

 

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git commit -am "test 1.1.2"

350731.png
등록 및 커밋

[master 80f8890] test 1.1.2

1 file changed, 1 insertion(+)

지금까지 생성한 태그 목록을 확인합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag

350761.png
태그 목록

1.0.0

1.1.0

1.1.1

이번에는 중복된 이름으로 태그를 생성해 보겠습니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag -a 1.1.1 -m "test 1.1.1"

350791.png
태그 생성

fatal: tag '1.1.1' already exists

350821.png
오류 발생

이미 태그 1.1.1이 있다는 오류 메시지를 출력합니다. 깃은 안정적인 배포 환경을 위해 이처럼 중복된 태그 이름을 사용하지 못하도록 태그 목록을 검사합니다.

10.5.5 태그 삭제

태그는 특정 커밋을 가리키는 꼬리표입니다. 실수로 생성할 태그의 커밋을 잘못 지정할 수도 있습니다. 이때는 기존에 생성한 태그를 삭제해야 합니다.

태그는 tag -d 명령어로 삭제할 수 있습니다.

$ git tag -d 태그이름

 

 

태그 목록에서 삭제된 태그 이름은 이후에 다시 사용할 수 있습니다.

지금까지 진행한 실습의 로그를 확인해 보겠습니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git log --oneline

350851.png
커밋 로그

80f8890 (HEAD -> master) test 1.1.2

f2691a0 (tag: 1.1.1) test 1.1.1

da8d211 (tag: 1.1.0) test 1.1.0

53028dc (tag: 1.0.0) test 1.0.0

3c92e35 first

커밋 f2691a0에 태그 1.1.1이 지정되어 있습니다. 태그 1.1.1을 삭제해 보겠습니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag -d 1.1.1

350891.png
태그 삭제

Deleted tag '1.1.1' (was b3ffc7d)

태그가 삭제되었습니다. 다시 로그를 확인합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git log --oneline

350921.png
커밋 로그

80f8890 (HEAD -> master) test 1.1.2

f2691a0 test 1.1.1

da8d211 (tag: 1.1.0) test 1.1.0

53028dc (tag: 1.0.0) test 1.0.0

3c92e35 first

추가된 태그가 커밋 로그에서도 삭제된 것을 확인할 수 있습니다. 태그 목록을 확인합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag

350952.png
태그 목록

1.0.0

1.1.0

태그는 단순히 커밋의 포인터이므로, 태그를 삭제해도 실제 커밋은 삭제되지 않습니다.

10.5.6 태그의 상세 정보 확인: show 명령어

Annotated 태그는 커밋의 태그 포인터와 함께 여러 정보를 포함합니다. tag 명령어는 태그의 목록만 출력할 뿐 상세 정보는 표시하지 않습니다. 태그의 상세 정보를 확인하려면 show 명령어를 사용해야 합니다.

$ git show 태그이름

 

 

다음과 같이 show 명령어를 실행하면 생성된 태그의 상세 정보를 확인할 수 있습니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git show 1.0.0

350982.png
태그 정보

tag 1.0.0

Tagger: hojin <infohojin@gmail.com>

Date: Thu May 23 18:12:16 2019 +0900

 

this is first tag

321626.png
태그 정보

 

commit 53028dc1486b42d23253ffd4001a758cef455372 (tag: 1.0.0)

Author: hojin <infohojin@gmail.com>

Date: Thu May 23 18:07:18 2019 +0900

test 1.0.0

 

diff --git a/version.htm b/version.htm

index 14f6513..eccf619 100644

--- a/version.htm

+++ b/version.htm

@@ -1 +1,4 @@

-<h1>태그 버전 실습 파일입니다.</h1>

\ No newline at end of file

+<h1>태그 버전 실습 파일입니다.</h1>

+<ul>

+ <li>버전 1.0.0 실습</li>

+</ul>

\ No newline at end of file

10.6

308958.png
309005.png
Lightweight 태그

git

 

Lightweight 태그는 가장 기본적인 태그입니다. Annotated 태그와 달리 버전 이름만 있습니다.

10.6.1 체크섬

Annotated 태그에는 커밋 해시 값과 부가적인 정보가 같이 있습니다. 반면 Lightweight 태그 방식은 커밋의 체크섬만 가지고 있습니다. 또 Annotated 태그에서 사용했던 -a, -m 같은 옵션은 사용할 수 없습니다.

$ git tag 태그이름

 

 

Lightweight 태그의 사용법은 간단합니다. 명령어 뒤에 태그 이름만 작성하면 됩니다. Lightweight 태그를 생성해 보겠습니다. 실습을 위해 version.htm 파일을 수정하고 저장한 후 커밋합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ code version.htm

351018.png
VS Code 실행

version.htm

<h1>태그 버전 실습 파일입니다.</h1>

<ul>

<li>버전 1.0.0 실습</li>

<li>버전 1.1.0 실습

 

<ul>

<li>수정 작업 1.1.1</li>

<li>수정 작업 1.1.2</li>

</ul>

</li>

<li>버전 2.0.0 lightweight 실습</li>

</ul>

 

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git commit -am "test 2.0.0"

351048.png
등록 및 커밋

[master 3ba46c0] test 2.0.0

1 file changed, 1 insertion(+)

새로 생성된 커밋에 Lightweight 태그를 생성합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag 2.0.0

321656.png
태그 이름만 작성

생성한 태그 목록을 확인합니다. 2.0.0 태그가 새로 추가되었습니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag

351078.png
태그 목록

1.0.0

1.1.0

2.0.0

321686.png
Lightweight 태그

10.6.2 태그의 상세 정보 확인

생성된 Lightweight 태그의 상세 정보를 확인해 보겠습니다. Annotated 태그와 동일하게 show 명령어를 사용합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git show 2.0.0

351108.png
태그 정보

commit 3ba46c0a20a9812341e057818ef155f6801d0760 (HEAD -> master, tag: 2.0.0)

321746.png
Lightweight 태그는 이 위치에 정보가 없음

 

Author: hojin <infohojin@gmail.com>

Date: Thu May 23 19:14:41 2019 +0900

test 2.0.0

diff --git a/version.htm b/version.htm

index 78de597..c9c61dc 100644

--- a/version.htm

+++ b/version.htm

@@ -7,4 +7,5 @@

<li>수정 작업 1.1.2</li>

</ul>

</li>

+ <li>버전 2.0.0 lightweight 실습</li>

</ul>

\ No newline at end of file

Annotated 태그와 달리 별도의 정보가 없는 것을 확인할 수 있습니다.

10.7

309039.png
309086.png
특정 커밋 태그

git

 

tag 명령어는 기본적으로 현재 HEAD가 가리키는 커밋을 기준으로 태그를 생성합니다. 현재 HEAD 포인터가 가리키는 커밋이 아닌 특정 커밋을 직접 지정하여 태그를 생성할 수 있습니다.

$ git tag -a 태그버전 커밋ID

 

 

특정 커밋을 지정하여 커밋을 생성할 때는 마지막 옵션으로 커밋 해시 값을 적습니다. 그러면 tag 명령어는 지정된 커밋 해시 값을 기준으로 새로운 태그를 생성합니다.

커밋을 지정해서 태그를 생성해 봅시다. 먼저 로그를 확인합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git log --oneline

351145.png
커밋 로그

3ba46c0 (HEAD -> master, tag: 2.0.0) test 2.0.0

80f8890 test 1.1.2

321778.png
이곳을 지정해서 생성함

f2691a0 test 1.1.1

da8d211 (tag: 1.1.0) test 1.1.0

53028dc (tag: 1.0.0) test 1.0.0

3c92e35 first

로그 기록 중 80f8890 커밋을 기준으로 새로운 태그를 생성합니다. 태그 이름은 1.1.2로 합니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git tag 1.1.2 80f8890

351175.png
커밋 지정한 태그

311379.jpg 그림 10-9 특정 커밋을 지정한 태그

317369.png 

태그를 생성한 후에 다시 로그를 확인합니다. 이전에 작성한 커밋에 새로운 태그가 추가되었습니다.

infoh@DESKTOP MINGW64 /e/gitstudy10 (master)

$ git log --oneline

351205.png
커밋 로그

3ba46c0 (HEAD -> master, tag: 2.0.0) test 2.0.0

80f8890 (tag: 1.1.2) test 1.1.2

f2691a0 test 1.1.1

da8d211 (tag: 1.1.0) test 1.1.0

53028dc (tag: 1.0.0) test 1.0.0

3c92e35 first

이처럼 태그는 특정 커밋을 지정하여 생성할 수도 있습니다.

10.7.1 소스트리에서 특정 커밋 지정

소스트리에서도 특정 커밋을 지정하여 태그를 생성할 수 있습니다. 가장 쉬운 방법은 그래프 목록에서 커밋을 선택하는 것입니다. 커밋을 클릭한 후 마우스 오른쪽 버튼을 눌러 명시적 커밋 메뉴를 선택합니다. 책에서는 test 2.0.0 커밋에서 마우스 오른쪽 버튼을 눌러 명시적 커밋 메뉴를 선택하고, 태그 이름에는 2.0.0을 입력합니다.

 

311187.jpg 그림 10-10 특정 커밋(test 2.0.0)의 태그 생성

1010.jpg
332007.png
 

마지막으로 태그 추가를 누르면 다음과 같이 2.0.0 태그가 생성됩니다.