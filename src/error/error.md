---
layout: home
---
## 오류 메시지 처리
## refusing to merge unrelated histories
만일 서로다른 두개의 프로젝트를 병합하고자 할때, 공통된 커밋이 존재하지 않는다. 따라서, 두개의 프로젝트는 기본적으로 병합을 할 수 없습니다.

하지만, `--allow-unrelated-histories` 은 이질적인 두개의 저장소의 history를 병합을 허용해주는 특수한 옵션입니다.


```
git merge 리모트/브랜치 --allow-unrelated-histories
```

덥어쓰기

```
git merge 20192/master --allow-unrelated-histories -X theirs
```


