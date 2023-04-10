---
layout: home
title: "지킬 빌드"
keyword: "지킬, jekyll"
---

# SiteMap 플러그인 설정

플러그인 설치
```
gem install jekyll-sitemap
```

## GemFile에 Plug-in 추가
사이트 내용 중 GemFile 에는 다음과 같이 추가한다.

```
# If you have any plugins, put them here!
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.6" 
  gem "jekyll-sitemap" 
end
```
## _config.yml 수정
_config.yml 을 다음과 같이 수정한다.

```
plugins:
  - jekyll-feed
  - jekyll-gist
  - jekyll-sitemap
```

Plug-In이 없이 추가할 수 있으나 Jekyll 3.4 버전 이후 부터는 해당 Plug-In을 사용할 수 있으므로 이 방법을 권장한다.
플러그인 없이 Jekyll Sitemap 만들기