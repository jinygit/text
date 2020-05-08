---
layout: home
title: "지킬 빌드"
keyword: "지킬, jekyll"
---

# 빌드
지킬을 이용하여 컨덴츠의 페이지를 생성하였다면, 두번재로 빌드를 통하여 실제 html 파일을 생성해 주어야 합니다. 

## 빌드 명령
콘솔에서 `build` 옵션을 이용하여 명령을 실행합니다.

```
Jekyll build
```

지킬은 현재 폴더의 컨덴츠 내용을 빌드한 결과를 `_site` 폴더로 출력을 합니다. 
만일, 다른 폴더에 html 결과물을 생성을 하고자 할때 는 `--destination` 옵션을 사용하시면 됩니다.

```
Jekyll build --destnation 출력폴더
```

<br>

## 소스변경
---
현재의 폴더의 컨덴츠 말고 다른 폴더에 컨덴츠가 저장되어 있는 경우 `--source` 옵션을 이용하여 직접 지정을 할 수도 있습니다.

```
Jekyll build --source 원본내용 --destnation 출력폴더
```

빌드 생성을 할 때 `--source` 와 `--destnation` 은 `_config.yml` 파일에 설정을 하여 실행을 할 수도 있습니다.

환경파일: _config.yml
```
source: _source
destination: _depoly
```
<br>

## 자동감지
컨덴츠를 작성하고 결과를 매번 build 하는 작업이 귀찬을 수 있습니다. 지킬은 컨덴츠의 내용을 자동으로 감지하여 생성된 컨덴츠를 자동 build 할 수 있도록 warch 기능을 제공합니다. 

```
Jekyll build –warch
```

단, 감지상태에서 자동빌드를 할 때 환경설정파일(_config.yml)파일은 자동으로 적용이 되지 않습니다. 
`_config.yml` 파일은 build 명령을 통하여 전체를 생성 할 때 적용이 됩니다.


