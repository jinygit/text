---
layout: home
title: "풀-리퀘스트"
keyword: "풀-리퀘스트,pull-request"
---

# 풀-리퀘스트
<hr>
깃은 분산형 버전 관리 시스템입니다. 분산되어 있는 저장소는 원격 저장소를 통하여 통합할 수 있습니다. 
이 과정에는 원격 저장소의 접근 권한이 필요합니다.

<br>

<h2>협업
    <small style="font-size: 0.5em;">>><a href="collaboration">학습하기</a></small>
</h2>
<hr>
깃허브는 분산되어 있는 저장소의 접근 권한의 문제를 해결하고, 불특정 다수를 대상으로 저장소를 병합할 수 있는 풀-리퀘스트 기능을 제공합니다. 깃허브는 풀-리퀘스트 기능을 사용하여 오픈 소스 생태계를 활성화에 큰 기여를 하게 됩니다. 또한, 깃허브가 대표적인 깃호스팅 서비스로 자리를 잡게 된 계기가 되었습니다.  

<br>

<h2>프로젝트
    <small style="font-size: 0.5em;">>><a href="project">학습하기</a></small>
</h2>
<hr>
풀리퀘스트를 실습할 수 있는 프로젝트를 탐색합니다. 또는 2개의 계정을 이용하여 프로젝트 실습 환경을 준비합니다.  

<br>

<h2>step1. 포크
    <small style="font-size: 0.5em;">>><a href="fork">학습하기</a></small>
</h2>
<hr> 
포크는 타인의 저장소를 수정 접근할 수 있도록 저장소를 복제하는 기능입니다.

* [코드 공유](fork#1)
* [접근 권한](fork#2)
* [포크 동작](fork#3)
* [포크 확인](fork#4)

<br>

<h2>step2. 복제
    <small style="font-size: 0.5em;">>><a href="clone">학습하기</a></small>
</h2>
<hr> 
포크된 저장소의 코드를 자신의 로컬 컴퓨터로 복제합니다.

* [포크 저장소](clone#1)
* [포크 내려받기](clone#2)

<br>

<h2>step3. 코드수정
    <small style="font-size: 0.5em;">>><a href="code">학습하기</a></small>
</h2>
<hr> 

* [계정 재등록](code#1)
* [코드 수정](code#2)
* [코드 전송](code#3)

<br>

<h2>step4. 요청
    <small style="font-size: 0.5em;">>><a href="request">학습하기</a></small>
</h2>
<hr> 

* [풀-리퀘스트](request#1)
* [요청](request#2)
* [메시지 작성](request#3)
* [확인](request#4)
* [통보](request#5)
* [쓰기 권한](request#6)

<br>

<h2>step5. 토론
    <small style="font-size: 0.5em;">>><a href="discuss">학습하기</a></small>
</h2>
<hr> 

* [아이디어](discuss#1)
* [wip](discuss#2)
* [댓글과 이슈](discuss#3)

<br>

<h2>step6. 코드리뷰
    <small style="font-size: 0.5em;">>><a href="review">학습하기</a></small>
</h2>
<hr> 

* [테스트](review#1)
* [변경 사항 체크](review#2)
* [diff](review#3)
* [그림](review#4)

<br>

<h2>step7. 테스트 및 검증
    <small style="font-size: 0.5em;">>><a href="test">학습하기</a></small>
</h2>
<hr> 

* [테스트 저장소](test#1)
* [포크 저장소 연결](test#2)
* [테스트 브랜치](test#3)
* [코드 테스트](test#4)
* [브랜치 제거](test#5)
* [병합](test#6)

<br>

<h2>step8. 코드반영
    <small style="font-size: 0.5em;">>><a href="receive">학습하기</a></small>
</h2>
<hr> 

* [pull-request](receive#1)
* [URL](receive#2)
* [conversation 탭](receive#3)
* [commit 탭](receive#4)
* [Files changed 탭](receive#5)
* [거절](receive#6)
* [재요청](receive#7)
* [승인](receive#8)
* [Create a merge commit](receive#9)
* [Squash and merge](receive#10)
* [Rebase and merge](receive#11)
* [충돌](receive#12)

<br>

<h2>관리
    <small style="font-size: 0.5em;">>><a href="manage">학습하기</a></small>
</h2>
<hr> 

* [포크 갱신](manage#1)
* [원본 저장소 추가](manage#2)
* [페치, 병합](manage#3)
* [포크 푸시](manage#4)
* [풀-리퀘스트 리버트](manage#5)
* [되돌리기](manage#6)
* [리버트](manage#7)
* [리버트 풀-리퀘스트](manage#8)

<br>

## 정리
<hr>
깃허브는 서로 간의 저장소를 공유하고, 복제하여 기여할 수 있는 오픈 소스 생태계를 지원합니다. 그리고 깃 자체만으로 힘든 원격 저장소 간의 복제와 병합을 쉽게 해줄 수 있는 풀-리퀘스트 기능의 서비스를 제공합니다.  

풀 리퀘스트는 최종적으로 권한이 없는 메인 저장소의 코드를 변경하는 것입니다. 불특정 대상으로 코드의 수정을 허용하기 위해서는 깃허브는 포크라는 원격 저장소의 복제와 병합 처리를 풀-리퀘스트라는 것으로 분리하였습니다. 여기서 앞에 풀(full)이란 포크 저장소 전체를 대상으로 하기 때문에 붙여진 이름입니다.  

풀-리퀘스트는 실제 실무 환경에서 이처럼 간단하지 않습니다. 수많은 의견과 충돌, 코드의 병합이 동시에 발생되고 해결을 요청합니다. 따라서 풀-리퀘스트를 요청할 때 충분한 테스트 과정을 거쳐서 문제가 발생되지 않도록 미연에 방지해야 합니다.  

<br><br>