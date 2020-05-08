---
layout: home
title: "지킬 구조"
keyword: "지킬, jekyll"
---

# 지킬 구조
이번에는 지킬의 내부 폴더 구조에 대해서 알아 봅니다. 지킬의 내부구조를 통하여 효율적인 정적 웹사이트를 생성할 수 있습니다.

지킬(jekll)의 주요 기능은 마크다운, 텍스트로 구성된 컨덴츠를 레이아웃과 결합 하여보기좋게 정적 HTML 파일을 생성하는 것입니다.

## 디렉토리 구조
작업 폴더에서 `tree`명령을 입력해 봅니다.

```
c:\jekyll>tree /f
windows 볼륨에 대한 폴더 경로의 목록입니다.
볼륨 일련 번호가 000000B4 447E:0DB0입니다.
C:.
│  .gitignore
│  404.html
│  about.md
│  Gemfile
│  Gemfile.lock
│  index.md
│  _config.yml
│
├─.sass-cache
│  ├─15209a447bbac67844d817c14c82736f5528653b
│  │      _base.scssc
│  │      _layout.scssc
│  │      _syntax-highlighting.scssc
│  │
│  └─a18dbbb8f958a9c4ec61fca2edd10d7d156591ba
│          minima.scssc
│
├─_posts
│      2017-10-18-welcome-to-jekyll.markdown
│
└─_site
    │  404.html
    │  feed.xml
    │  index.html
    │
    ├─about
    │      index.html
    │
    ├─assets
    │      main.css
    │
    └─jekyll
        └─update
            └─2017
                └─10
                    └─18
                            welcome-to-jekyll.html
```

위와 같은 폴더 구조를 확인할 수 있습니다.
