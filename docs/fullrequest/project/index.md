# 프로젝트
깃허브에는 수많은 오픈 소스 프로젝트들이 있습니다. 
`풀-리퀘스트`를 실습하기 위해서는 대상이 되는 오픈 소스 프로젝트가 필요합니다.

## 제약 사항
깃과 깃허브를 학습한 후에 풀-리퀘스트를 실제로 경험해본 개발자는 제한적입니다. 
풀-리퀘스트는 권한이 없는 저장소에 자신의 개인 저장소를 병합하는 요청이기 때문입니다.

많은 개발자가 풀-리퀘스트의 경험이 없는 이유는 풀-리퀘스트 요청을 하여도 대부분의 요청을 거절하기 때문입니다. 

풀-리퀘스트가 반영되기 위해서는 코드의 버그를 수정하거나, 공감대가 있는 문제점을 개선하는 적합한 코드여야 합니다. 
또한, 코드를 반영하는 과정에서 수많은 코드 리뷰와 토론이 이루어집니다.

또는 오픈 소스의 그룹이 개발 멤버가 아니기 때문입니다. 
검증되지 않은 개발자로부터 외부 코드를 병합할 때 발생할 수 있는 문제점들을 미연에 방지하기 위해서입니다.

이처럼 풀-리퀘스트를 경험해보기 위해서는 여러 제약 사항들이 있습니다. 이는 바로 프로젝트 참여로 이어지게 됩니다.

## 실습 환경
풀-리퀘스트를 실습해보는 방법은 2가지입니다. 

첫 번째로, 자신의 코드를 무난하게 받아들여줄 메인 프로젝트를 선정하는 것입니다. 하지만 이는 쉽지 않습니다. 
자신의 실력과 코드를 상대방에게 검증을 받아 통과한다는 것은 꽤 난이도가 있는 작업입니다.  

둘째로, 직접 자신이 메인 프로젝트를 만드는 것입니다. 이를 위해서는 2개의 계정이 필요합니다. 
또한, 각 계정은 서로 접속 권한을 가지고 있지 않습니다. 하나는 메인 프로젝트용과 하나는 포크용 계정입니다. 
깃허브는 이메일 주소를 기반으로 회원 가입을 할 수 있습니다.  

2개 이상의 이메일을 가지고 있다면 쉽게 2개의 계정을 생성하여 실습할 수 있을 것입니다. 
또는 같이 학습할 친구 한 명을 두어 서로 연습해보는 것도 좋습니다.

세 번째로 필자가 운영하는 메인 프로젝트에 참여해보는 것도 방법입니다. 
다음 절에서 생성한 코드를 깃 저장소에 운영하고 있습니다. 

```
https://github.com/jinygit/hello.git
```

이 저장소의 주소를 포크하여 실습할 수도 있습니다. 
만일 PHP 언어가 익숙한 개발자라면 필자의 오픈 소스 프로젝트 참여해도 괜찮은 방법입니다.

```
https://github.com/jinyphp
```

지니PHP는 깃허브와 연계하여 PHP 기반의 정적 웹 사이트를 구축할 수 있는 도구입니다.

## 메인 저장소
실습을 위한 메인 프로젝트 저장소를 하나 생성해봅니다. 필자의 저장소를 이용하는 경우 이 과정은 넘어가도 됩니다.  
저장소를 하나 생성합니다.

```
$ git init hello

Initialized empty Git repository in E:/jinygit/hello/.git/
$ cd hello/
```

새로운 예제 파일 하나를 생성합니다. 코드 생성과 커밋합니다. 

README.md
```md
# pull-request 인사를 하세요.
```

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/hello (master)
$ git add README.md

infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/hello (master)
$ git commit -m "first"
[master (root-commit) b93e6ed] first
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
```

깃허브에서 새로운 메인 저장소로 사용할 저장소를 하나 생성합니다. 
원격 저장소를 등록한 후에 푸시합니다.

![풀리퀘스트](./img/image001.png)
 
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit_hello (master)
$ git remote add origin https://github.com/jinygit/hello.git

infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit_hello (master)
$ git push -u origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 263 bytes | 263.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/jinygit/hello.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

깃허브 저장소를 확인해봅니다. 
푸시한 README.md 파일을 메인 화면에 출력합니다.

![풀리퀘스트](./img/image002.png) 

필자가 생성한 메인 저장소의 주소는 `https://github.com/jinygit/hello.git`입니다.
