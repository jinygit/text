---
layout: home
title: "지킬 빌드"
keyword: "지킬, jekyll"
---

# SEO 설정

seo 플러그인을 설치합니다.
```
gem install jekyll-seo-tag
```

`_config.yml` 설정을 합니다.
```yml
plugins:
  - jekyll-seo-tag
```

레이아웃 `<head></head>` 영역에 다음과 같이 코드를 추가합니다.
```
{% seo title=false %}
```