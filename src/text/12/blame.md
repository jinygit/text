---
layout: home
title: "Git 교과서"
keyword: "git, 깃사용법, 깃허브, 소스트리, 깃교과서"
---

# 파일 애너테이션
---
개발하다 보면 코드를 잘못 작성해서 오류가 발생하곤 합니다. 하지만 여러 개발자와 협업하다 보
면 잘못된 코드를 찾는 것이 쉽지 않습니다.

<br>
<a name="1"></a>

## blame
---
잘못된 코드가 어디서부터 시작되었는지 찾기 어렵습니다. 잘못된 내용을 찾으려면 모든 커밋 이
력을 살펴보아야 하는데, 생각보다 시간이 오래 걸립니다. 깃은 이러한 코드를 쉽게 찾을 수 있게
파일의 수정 이력을 분석합니다. 그리고 blame 기능은 커밋의 메타 정보를 코드 라인별로 같이
결합하여 출력합니다. 코드를 수정한 사람이 누구인지, 언제 수정한지를 쉽게 판별할 수 있으며,
메타 정보를 바탕으로 문제를 좀 더 쉽게 파악할 수 있습니다.

<br>
<a name="2"></a>

## 실습 환경 준비
---
blame 기능을 실습하기 위해 index.htm 파일을 수정한 후 커밋해 보겠습니다.

VS Code 실행
```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ code index.htm
```

index.htm
```html
<h1>hello world</h1>
```

등록 및 커밋
```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git commit -am "add h1 tag" 
[master 520aadf] add h1 tag
1 file changed, 1 insertion(+), 1 deletion(-)
```

VS Code 실행
```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ code index.htm 
```

index.htm
```html
<h1>hello world</h1>
```

깃을 이용하여 코드 이력을 관리할 수 있습니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git commit -am "add description" 등록 및 커밋
[master 023dade] add description
1 file changed, 2 insertions(+), 1 deletion(-)
```

VS Code 실행
```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ code index.htm 
```

index.htm
```html
<h1>hello world</h1>
```

깃을 이용하여 코드 이력을 관리할 수 있습니다.
깃은 ref를 참조하여 작업이 이루어집니다.  

```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git commit -am "ref description" 등록 및 커밋
[master 71099d0] ref description
1 file changed, 2 insertions(+), 1 deletion(-)
```

<br>
<a name="3"></a>

## blame 명령어
---
blame 명령어는 개별 파일에서만 동작하며, 명령어 인자 값으로 개별 파일을 전달합니다.

```
$ git blame 파일이름
```

작성한 파일의 blame을 확인해 봅시다.

```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git blame index.htm 메타 정보 출력
023dadec (hojin 2019-05-26 16:19:05 +0900 1) <h1>hello world</h1>
71099d05 (hojin 2019-05-26 16:31:18 +0900 2) 깃을 이용하여 코드 이력을 관리할 수 있습니다.
71099d05 (hojin 2019-05-26 16:31:18 +0900 3) 깃은 ref를 참조하여 작업이 이루어집니다.
```

출력 결과를 보니 각 커밋에 대한 해시 값, 작성자, 코드 등 내용도 함께 보여 주네요. blame은
누가 코드의 어느 라인을 수정했는지 파악할 때 유용합니다.

<br>
<a name="4"></a>

## 옵션 활용
---
소스 코드의 용량이 클 때는 이력 정보도 많이 출력됩니다. 이때는 -L 옵션을 사용하여 파일의 특
정 영역만 지정할 수 있습니다.

```
$ git blame -L 시작줄, 마지막줄 파일이름
```

파일을 수정한 히스토리를 출력해 보겠습니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy12 (master)
$ git blame -L 2,3 index.htm 메타 정보 필터링
71099d05 (hojin 2019-05-26 16:31:18 +0900 2) 깃을 이용하여 코드 이력을 관리할 수 있습니다.
71099d05 (hojin 2019-05-26 16:31:18 +0900 3) 깃은 ref를 참조하여 작업이 이루어집니다.
```

blame 기능은 파일에서 특정한 수정 사항 및 커밋들을 찾는 데 매우 유용합니다. 개발 과정에서
만든 수많은 코드 중 수정한 부분만 쉽게 찾아낼 수 있습니다.  

blame 명령어는 옵션을 사용하면 좀 더 다양하게 검색할 수 있습니다.  
* -e: 사용자 이름 대신 이메일을 출력합니다.
* -w: 공백 문자를 무시합니다.
* -M: 같은 파일 내에서 복사나 이동을 감지합니다.
* -C: 다른 파일에서 이동이나 복사된 것을 감지할 수 있습니다.

<br><br>