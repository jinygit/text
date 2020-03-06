# 리모트
원격저장소의 리모트도 `Refs` 에 저장됩니다.

## 리모트 ref
리모트 `ref`는 원격 저장소로 푸시(push)된 마지막 커밋을 저장하는 refs 입니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ ls .git/refs/
head/  heads/  master  tags/
```
아직 remotes 는 폴더는 존재하지 않습니다.

푸시를 하는 순간, 로컬 저장소에는 리모트 refs 가 생성이 됩니다.  
리모트는 원격 저장소로 푸시(push)시 마다 각 브랜치의 마지막 커밋을 `refs/remotes` 에 저장을 합니다.

## 서버 푸시
새로운 깃허브 원격 저장소를 하나 생성하여 추가합니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git remote add origin https://github.com/jinygit/gitstudy19.git
```

원격 저장소를 추가 하였다고 해서 remotes 폴더가 생성되지는 않습니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ ls .git/refs/
head/  heads/  master  tags/
```

직접 저수준 명령을 통하여 작업을 하였기 때문에 아직 master 브랜치가 만들어 지지 않았습니다.  
업로드를 위해서 master 브랜치를 추가로 생성합니다. 우리는

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git branch master
```

서버에 푸시를 합니다.
```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ git push -u origin master
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (6/6), 513 bytes | 102.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To https://github.com/jinygit/gitstudy19.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

로컬 저장소에서 푸시(push)를 하게 되면, 서버와 마지막으로 통신된 커밋을 `refs/remotes/origin/master`에 `refs`로 저장을 하게 됩니다.

```
infoh@DESKTOP-VAKLOFQ MINGW64 /e/jinygit/gitstudy19 (master)
$ cat .git/refs/remotes/origin/master
0ee97afec0380e074080129b339e5d284f4ba7d9
```

리모트의 `refs`는 읽기 전용입니다.  
리모트 `refs`를 통하여 체크아웃 같이 브랜치를변경을 할 수는 없습니다. 북마크와 같습니다.

