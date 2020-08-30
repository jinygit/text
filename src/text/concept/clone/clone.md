---
layout: home
title: "깃 저장소 복제"
keyword: "복제, clone"
breadcrumb:
- "text"
- "concept"
- "clone"
---

# 복제 명령어
---
깃의 저장소를 복제하는 명령어는 `clone`입니다.  

<br>

## 저장소 URL
---
복제하려면 공개된 저장소의 URL이 필요합니다. 복 

제할 때 폴더 이름을 지정하지 않으면 공개 저장소에서 사용된 폴더와 `동일한 이름`으로 `새 폴더`를 만듭니다.  
다른 이름으로 복제하길 원한다면 새 폴더 이름을 추가 `인자`로 적어 줍니다.  

```
$ git clone 원격저장소URL 새폴더이름
```

<br>

## 복제 실습
---
다음은 필자가 운영하는 jinyphp 오픈 소스 사이트의 주소를 이용하여 저장소를 복제하는 예입니다.  
새 폴더 이름을 적지 않아 공개 저장소에서 사용된 폴더와 동일한 이름으로 새 폴더를 만들 것입니다.  

```
$ git clone https://github.com/jinyphp/jiny
Cloning into 'jiny'...
remote: Enumerating objects: 975, done.
remote: Total 975 (delta 0), reused 0 (delta 0), pack-reused 975
Receiving objects: 100% (975/975), 4.98 MiB | 3.67 MiB/s, done.
Resolving deltas: 100% (307/307), done.
```

`git clone` 명령어를 사용하면 깃은 자동으로 깃 서버에 접속합니다.  
그리고 저장소의 모든 소스 코드를 `자동`으로 내려받습니다.  

<br> 

## 저장소 이름 변경
---
깃은 저장소 안에 있는 파일들과 `.git `리포지터리를 기반으로 이력을 관리합니다.  
따라서 복제한 후에는 복제된 폴더 이름을 그대로 사용하지 않아도 됩니다. 
필요에 따라 깃의 폴더 이름을 변경해도 괜찮습니다.  

<br><br>