---
layout: home
title: "지킬"
keyword: "jekyll, 지킬, 테마, 루비, ruby"
---

# 지킬(jekyll)
---
지킬은 루비로 제작된 정적 웹사이트 빌드도구 입니다. 깃허브는 정적사이트의 생성 도구로 지킬을 사용합니다. 

* 지킬설치
* [테마](theme)

<br>

## 지킬 패키지 설치
---
지킬을 사용하기 위해서는 `루비`언어가 설치되어 있어야 합니다. 루비가 설치가 되어 있다면, 루비 패키지 메니저 `gem`을 사용하여 지킬을 설치할 수 있습니다. 터미널창을 실행한 후에 다음과 같이 입력을 합니다.

```
gem install jekyll
```

<br>

## 지킬 공식사이트
---
지킬을 이용하여 웹사이트를 만들고, 화면을 처리하여 깃 저장소에 등록을 하시면 멋진 정적 웹사이트를 운영할 수 있습니다. 
보다 자세한 것은 https://jekyllrb.com/ 를 참고하시길 바랍니다. 

![지킬_공식사이트](./img/jekyll_00.png)

<br>

## 기본 템플릿 생성
---
지킬을 이용하여 웹사이트의 기본 템플릿을 생성할 수 있습니다. 현재의 폴더에 제킬 프로젝트 사이트 하나를 생성해 봅니다.

```
c:\jekyll>jekyll new 폴더명
```

지정한 폴더명으로 새로운 템플릿 사이트를 생성합니다. 만일 현재의 폴더에 생성을 할때에는 폴더명 대신에 `.`을 사용합니다.

```
c:\jekyll>dir/w
 C 드라이브의 볼륨: windows
 볼륨 일련 번호: 447E-0DB0

 c:\jekyll 디렉터리

[.]           [..]          .gitignore    404.html      about.md      Gemfile       index.md      _config.yml
[_posts]
               6개 파일               3,801 바이트
               3개 디렉터리  18,317,680,640 바이트 남음
```

<br>

## 서버실행
---
생성한 템플릿 사이트를 로컬컴퓨터에서 실행해 보도록 합니다. 지킬은 자신의 컴퓨터를 웹서버로 구동을 할 수 있는 `serve` 명령을 제공합니다.

```
c:\jekyll>jekyll serve
Configuration file: c:/jekyll/_config.yml
            Source: c:/jekyll
       Destination: c:/jekyll/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.631 seconds.
  Please add the following to your Gemfile to avoid polling for changes:
    gem 'wdm', '>= 0.1.0' if Gem.win_platform?
 Auto-regeneration: enabled for 'c:/jekyll'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

이와 같이 출력되면 콘솔을 닫지 말고 표기된 IP주소와 포트로 브라우저 접속을 해봅니다.  
http://127.0.0.1:4000/

제킬(Jekyll)로 생성된 정적 웹페이지를 확인해 보실 수 있습니다. 

<br>

## 오류해결
---
만일 지킬 내장 웹서버를 실행시 다음과 같은 오류가 발생할 수 있습니다.

```
C:/Ruby24-x64/lib/ruby/2.4.0/rubygems/core_ext/kernel_require.rb:55:in `require': cannot load such file -- bundler (LoadError)
        from C:/Ruby24-x64/lib/ruby/2.4.0/rubygems/core_ext/kernel_require.rb:55:in `require'
        from C:/Ruby24-x64/lib/ruby/gems/2.4.0/gems/jekyll-3.6.0/lib/jekyll/plugin_manager.rb:48:in `require_from_bundler'
        from C:/Ruby24-x64/lib/ruby/gems/2.4.0/gems/jekyll-3.6.0/exe/jekyll:11:in `<top (required)>'
        from C:/Ruby24-x64/bin/jekyll:23:in `load'
        from C:/Ruby24-x64/bin/jekyll:23:in `<main>'
```

이런경우 추가 패키지를 설치하고 다시 실행을 해보면 문제를 해결 할 수 있습니다.

```
c:\jekyll>gem install bundler
Fetching: bundler-1.20.4.gem (100%)
Successfully installed bundler-1.20.4
Parsing documentation for bundler-1.20.4
Installing ri documentation for bundler-1.20.4
Done installing documentation for bundler after 16 seconds
1 gem installed

c:\jekyll>bundle install
Fetching gem metadata from https://rubygems.org/...........
Fetching version metadata from https://rubygems.org/..
Fetching dependency metadata from https://rubygems.org/.
Resolving dependencies...
Using public_suffix 3.0.0
… 중간생략
Installing minima 2.1.1
Bundle complete! 4 Gemfile dependencies, 25 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
```

다시 jekyll serve 를 실행해 봅니다.

<br><br>