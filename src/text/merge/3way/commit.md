---
layout: home
title: "3-way 병합"
keyword: "3-way 병합"
breadcrumb:
- "text"
- "merge"
- "commit"
---

## 병합 커밋
---
병합은 각 브랜치에서 독립적으로 작업된 소스를 파일 하나로 결합합니다. 하지만 브랜치별로 각각 작업한 내용을 병합하는 과정은 힘들고 어렵습니다. 하지만 깃을 사용하면 복잡한 병합도 좀 더 손쉽게 처리할 수 있습니다.  

3-way 병합은 두 브랜치에서 공통 조상 커밋을 자동으로 찾아 주며, 공통 조상 커밋을 기준으로 브랜치를 병합합니다. 그리고 병합을 성공적으로 완료한 후에는 새로운 커밋을 추가로 하나 생성합니다. 새로 생성된 커밋을 병합 커밋이라고 합니다. 병합 커밋은 부모 커밋이 2개라는 특징이 있습니다.  

그림 8-19] 병합 커밋  
![병합 커밋](./img/08-19.jpg)


그럼 앞에서 실습한 hotfix 브랜치를 master 브랜치에 병합해 봅시다. hotfix 브랜치를 병합하려면 먼저 기준이 되는 master 브랜치로 체크아웃해야 합니다. 다른 브랜치에 있다면 git checkout master로 체크아웃하세요.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master) ☜ 기준 브랜치
$ git merge hotfix ☜ 기준 브랜치에 hotfix를 병합
Auto-merging index.htm
Merge made by the 'recursive' strategy.
 index.htm | 3 +++
 1 file changed, 3 insertions(+)
```

3-way 방식으로 hotfix 브랜치와 master 브랜치를 병합했습니다. 그림으로 병합 구조를 나타내면 그림 8-20과 같습니다.  

그림 8-20] hotfix 브랜치의 3-way 병합  
![hotfix 브랜치의 3-way 병합](./img/08-20.jpg)

성공적으로 병합한 후에는 커밋 로그를 확인합니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git log -1
commit a48d563373f777f5f19a1ad9426297c5bc31d01c (HEAD -> master)
Merge: 8583edf 7277f2d
Author: hojin <infohojin@gmail.com>
Date:   Fri May 17 16:30:07 2019 +0900
    Merge branch 'hotfix'
```

새로운 병합 커밋이 하나 추가되었습니다. 소스트리에서도 병합된 모습을 확인할 수 있습니다.  

그림 8-21] 소스트리에서 병합 커밋 확인  
![소스트리에서 병합 커밋 확인](./img/08-21.jpg)

<br>