# 테그
커밋은 트리객체를 기반으로 생성합니다. 그리고 테그는 커밋 객체를 기반으로 생성됩니다.

## lightweight
태그는 크게 annotated 태그와 lightweight 테그로 구분합니다. update-ref 명령을 이용하여 테그 포인터를 생성할 수 있습니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git update-ref refs/tags/1.0 0ee97afec0380e074080129b339e5d284f4ba7d9
```

간단한 lightweight 테크를 만들어 보았습니다. Lightweight 테그는 커밋 객체의 sha1 해쉬값을 가지고 있습니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ cat .git/refs/tags/1.0
0ee97afec0380e074080129b339e5d284f4ba7d9
```

생성된 테그를 확인해 봅니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git tag
1.0
```

## annotated
annotated 태그는 좀더 복잡하게 동작을 합니다. 새로운 추가 annotated 테그를 생성해 봅니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git tag -a 1.1 0ee97af -m "anno tag"
```

생성된 테그의 정보를 확인해 봅니다. 앞에서 lightweight 테그와 달리 커밋 해쉬값이 아닌 새로운 해쉬값으로 들어간 것을 볼 수 있습니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ cat .git/refs/tags/1.1
3b9fa13c10c7744fdf611a77a2ac4db792c0baac
```

Annotated 테그를 생성하게 되면 깃은 새로은 테그 객체을 추가로 생성하게 됩니다. 그리고 생성된 테그 객체의 해쉬 값을 저장합니다. 생성된 테그 객체를 확인해 봅니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git cat-file -p 3b9fa13c10c7744fdf611a77a2ac4db792c0baac
object 0ee97afec0380e074080129b339e5d284f4ba7d9
type commit
tag 1.1
tagger hojin <infohojin@gmail.com> 1550483768 +0900

anno tag
```
테그는 커밋에 다는 것이 아닙니다. 이처럼 테그 객체를 생성하거 테그를 달게 됩니다.


