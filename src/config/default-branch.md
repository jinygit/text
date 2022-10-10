# 기본 브랜치 설정
깃의 `init` 명령은 깃저장소를 초기화 합니다. 기본적으로 깃이 저장소를 초기화 할때 `master` 브랜치를
기본적으로 생성해 주지만, 깃허브와 같은 서비스는 `master` 브랜치 대신에 `main` 브랜치를 사용하기도 합니다.

이를 위해서 깃의 기본 브랜치를 직접 설정해 주어야 하는 경우도 발생합니다.

## 실습하기
다음은 우분투 22.04에서 기본 설정된 깃 시스템에서 `git init`명령을 실행한 예 입니다.

```bash
jinyerp@jinyerp:/var/www/jinyerp/tms/Modules/UIBootstrap$ git --version
git version 2.34.1
```

여기서 깃 init 명령을 실행하여 저장소를 초기화 해보도록 합니다.

```bash
jinyerp@jinyerp:/var/www/jinyerp/tms/Modules/UIBootstrap$ git init .
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint:   git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint:   git branch -m <name>
Initialized empty Git repository in /var/www/jinyerp/tms/Modules/UIBootstrap/.git/
```

저장소가 생성이 되었지만, 기본 브랜치가 설정이 되어 있지 않다고 표시됩니다.

## 기본 브랜치 설정
깃은 config 명령을 통하여 다양한 시스템 환경 설정을 합니다. 
`init.defaultBranch` 설정옵션을 통하여 기본 브랜치를 설정합니다.

```
git config --global init.defaultBranch <name>
```

저는 이전처럼 `master`브랜치를 선호하기 때문에 master로 설정을 해보도록 합니다.

```
git config --global init.defaultBranch master
```

이제 깃을 통하여 초기화 할때, 기본 브랜치가 master로 설정이 될 것입니다.


