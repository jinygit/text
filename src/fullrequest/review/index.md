# 코드 리뷰
코드를 수정하였다면 풀-리퀘스트를 보내기 전에 충분히 리뷰하는 것이 좋습니다.

## 테스트
자신의 코드가 정상적으로 동작하고 있는지, 오류가 없는지 확인합니다. 또는 팀원 단위로 작업하는 경우에는 다른 팀원에게도 함께 테스트해줄 것을 요청하는 것도 좋습니다.

대형 프로젝트의 경우 중간 관리자를 두어 코드 리뷰를 받는 경우도 있습니다. 메인 프로젝트 담당자는 수많은 코드의 풀-리퀘스트를 받으며 이를 매번 검토, 테스트할 수 없습니다. 또한, 시간이 많이 소요됩니다. 

이러한 요청 전의 코드 리뷰는 많은 검토 과정을 줄이고 효율화할 수 있습니다.

## 변경 사항 체크
코드를 리뷰할 때는 변경 사항을 위주로 체크합니다. 수정한 부분의 기능이 잘 동작하는지 확인합니다. 수정 부분으로 다른 부분의 코드가 동작하는 데 영향이 없는지도 같이 확인합니다.

코드를 검토할 때 의견이 있다면 풀-리퀘스트에 댓글을 남일 수 있습니다.

이렇게 댓글을 작성하면 깃허브는 코드 수정자에게 메일로 알람을 발송하게 됩니다.

## diff
코드의 변경 사항을 확인할 때 diff 기능을 이용하면 편리합니다.

diff는 원본과 수정본의 코드 차이점들을 찾아 출력합니다. 어떠한 코드가 어떻게 변경이 되었는지를 쉽게 파악할 수 있습니다.

## 그림
깃허브는 텍스트 형태의 코드뿐만 아니라 그림 파일도 변경 사항을 비교하여 확인할 수 있습니다.

그림을 비교하는 방법은 크게 3가지를 지원합니다.
* 2-up
* Swipe
* Onion skin

2-up은 두 개의 그림을 좌/우로 출력하여 비교하는 방법입니다. Swipe는 두 개의 그림을 겹쳐서 경계선을 이용하여 그림을 검사할 수 있습니다. Onion skin은 두 이미지를 겹쳐서 투명도를 조절하여 비교하는 방법입니다.