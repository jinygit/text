
# HEAD
HEAD는 브랜치의 마지막 커밋을 가리키고 있습니다. HEAD는 refs로 간접적인 심볼(symbolic)값 입니다.

## 심볼
저장소의 HEAD 값을 확인해 봅니다. HEAD에는 SHA1 해쉬값이 없습니다. 대신에 간적접인 refs 값이 들어가 있습니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/gitstudy19 (master)
$ cat .git/HEAD
ref: refs/heads/master
```

브랜치는 각 브랜치의 마지막 커밋을 HEAD로 표시를 합니다. 새로운 브랜치로 체크아웃을 하게 되면 깃은 간접 refs의 값으로 HEAD를 변경합니다.

## symbolic-ref
HEAD의 파일을 직접 수정하고 읽을 수 있습니다. 깃은 HEAD의 값을 읽을 수 있는 별도의 저수준 symbolic-ref 명령을 제공합니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/gitstudy19 (master)
$ git symbolic-ref HEAD
refs/heads/master
```

HEAD의 값을 직접 읽을 때 발생할 수 있는 문제를 미연에 방지하기 위해서 입니다.

또한 HEAD를 설정할 때 잘못된 refs에 대한 오류 필터링을 통하여 안전한 갱신을 도와줍니다.
