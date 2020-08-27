---
layout: git
title: "diff"
keyword: "diff"
breadcrumb:
- "commit"
- "diff"
- "difference"
---

# 커밋 간 차이
---
스테이지 영역에 있는 수정된 파일을 아직 커밋하지 않았다면, 최신 커밋과 변경 내용을 비교하여 볼 수 있습니다.  
`HEAD`는 마지막 커밋을 가지고 있는 포인터입니다.  

워킹 디렉터리와 마지막 커밋을 비교해 봅시다.  

```
infoh@hojin MINGW64 /e/gitstudy04 (master)
$ git diff head ☜ head 포인터를 입력
diff --git a/index.htm b/index.htm
index f5097d9..56af0de 100644
--- a/index.htm
+++ b/index.htm
@@ -7,5 +7,6 @@
 </head>
 <body>
     <h1>hello GIT world!</h1>
+    <h2>깃을 이용하면 소스의 버전 관리를 쉽게 할 수 있습니다.</h2>
 </body>
 </html>
\ No newline at end of file
```

`HEAD`는 최근의 커밋 중 가장 마지막 커밋의 위치를 가리키는 값입니다.  
`HEAD`를 이용하면 최신 커밋과 이전 커밋을 비교하여 출력할 수 있습니다.  

<br>