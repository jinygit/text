---
layout: home
title: "diff"
keyword: "diff"
breadcrumb:
- "commit"
- "diff"
- "stage"
---


# 워킹 디렉터리 vs 스테이지 영역
---
아직 add 명령어로 파일을 추가하지 않은 경우, 워킹 디렉터리와 스테이지 영역 간 변경 사항을 비교할 수 있습니다.  

index.htm 파일을 열어 `<h1>` 태그 밑에 `<h2>` 태그와 내용을 추가합니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ code index.htm
```
 

```html
<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>JINYGIT</title>

</head>

<body>

<h1>hello GIT world!</h1>

<h2>깃을 이용하면 소스의 버전 관리를 쉽게 할 수 있습니다.</h2>

</body>

</html>
```
 

그리고 diff 명령어를 실행해 봅시다.  
```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git diff ☜ 스테이지 vs 워킹 디렉터리 비교.
diff --git a/index.htm b/index.htm
index f5097d9..56af0de 100644
--- a/index.htm
+++ b/index.htm
@@ -7,5 +7,6 @@
 </head>
 <body>
     <h1>hello GIT world!</h1>
+    <h2>깃을 이용하면 소스의 버전 관리를 쉽게 할 수 있습니다.</h2> ☜ 추가
 </body>
 </html>
\ No newline at end of file

```

이처럼 워킹 디렉터리 내용과 스테이지 내용의 차이점을 출력합니다.  

이번에는 변경한 파일을 `add` 명령어로 추가하여 스테이지 영역에 등록합시다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git add index.htm
```

그런 다음 다시 diff 명령어를 수행합니다.  
아무 내용도 출력되지 않습니다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git diff
```

이것은 등록 과정을 거쳐 워킹 디렉터리의 수정 내역을 스테이지 영역에 반영했기 때문입니다.  
따라서 아무 내용도 출력되지 않습니다.  

<br>

