---
layout: home
title: "깃 빈커밋 작성하기"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
description: "--allow-emplty 옵션을 사용하면 비어 있는 커밋 메시지를 작성할 수 있습니다."
breadcrumb:
- "commit"
---

# 빈 커밋작성
---

커밋은 변경된 내용을 깃 저장소에 알려주는 명령어 입니다. 파일의 변경사항이 있어야만 커밋할 내용이 생기게 됩니다.

하지만, 파일의 변경내용이 없이도 비어있는 커밋 기록을 할 수 있습니다. 이때 사용하는 명령어는 `--allow-emplty` 입니다.

```bash
$ git commit --allow-empty -m "empty commit"
```

<br><br>