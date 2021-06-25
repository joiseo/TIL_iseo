## branch command

- 브랜치 생성

```bash
$ git branch 브랜치명
```

```bash
iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (master)
$ git branch login
```



- 브랜치 목록

```bash
$ git branch
```

```bash
iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (master)
$ git branch
Cygwin WARNING:
  Couldn't compute FAST_CWD pointer.  This typically occurs if you're using
  an older Cygwin version on a newer Windows.  Please update to the latest
  available Cygwin version from https://cygwin.com/.  If the problem persists,
  please see https://cygwin.com/problems.html

  login
* master
```



- 브랜치 이동

```bash
# git checkout 까지만 입력한 상태에서
# tab*2 -> checkout 가능한 브랜치명 확인 가능
$ git checkout 브랜치명
(브랜치명) $
```

```bash
iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (master)
$ git checkout
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (master)
$ git checkout
HEAD            master          origin/master
login           origin/HEAD

```

```bash
$ git log --oneline
29c46b5 (HEAD -> master) modified 01_git
0d37e99 (origin/master, origin/HEAD) Create README.md

```

- login branch를 만든 시점이 중요! masterbranch를 먼저 생성을 하고 그 위에 로그인브랜치를

  생성해서 작업해야 모든 내용들이 적용이 된다.

  - HEAD : 현재 우리가 속한 위치

- 브랜치 생성 + 이동

```bash
$ git checkout -b 브랜치명
```

```bash
iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (master)
$ git checkout login
Switched to branch 'login'

iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (login)
$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

```

```bash
iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (login)
$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
# git checkout login 으로 해서 새로운 파일 login.py을 만들어 준 뒤에 add하고 그 뒤에 마무리로 커밋 ($ git commit -m "create login.py")까지 완료하고 
# git checkout master로 돌아왔을 때 마치 로그인에서 만들었던 파일이 사라진 것처럼보인다
# 그렇다면 로그인에서 작업한 파일은 사라진 것일까? 답은 : N
#
```

# git log --all --graph --oneline

```bash
iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (master)
$ git log --all --graph --oneline

* 57ad14e (HEAD -> master) create master.py
| * 4b42b8d (login) modified a.txt   #graph형식으로 나타남 || 이런거~
| * f12756d create login.py
|/
* 29c46b5 modified 01_git
* 0d37e99 (origin/master, origin/HEAD) Create README.md
* 4c4a96f test commit
* 8fea96e 210624 | push file.md
* ce0fce5 210624 | created CLI.md
* 6c73087 210624 | created CLI.md

```



# touch

- 파일만드는 명령어

### 브랜치 병합

```bash
(master) $ git merge 브랜치명 
```

- 반드시 master브랜치에 브랜치를 병합

```bash
$ git merge branch 'login' (실습)
```

- 왜 합치는지 commit message를 남기기위해서(새로운 버전을 왜 만드는지) 1.i누르고 2. INSERT쓰면 3.ESC누르고 4. 수정사항없으면 :(세미콜론)wq
- $ git log --all --graph --oneline (변경사항 그래프로 알아보기)

```bash
iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (master)
$ git log --all --graph --oneline
Cygwin WARNING:
  Couldn't compute FAST_CWD pointer.  This typically occurs if you're using
  an older Cygwin version on a newer Windows.  Please update to the latest
  available Cygwin version from https://cygwin.com/.  If the problem persists,
  please see https://cygwin.com/problems.html

*   f164dd1 (HEAD -> master) Merge branch 'login'
|\
| * 4b42b8d (login) modified a.txt
| * f12756d create login.py
* | 57ad14e create master.py
|/
* 29c46b5 modified 01_git
* 0d37e99 (origin/master, origin/HEAD) Create README.md
* 4c4a96f test commit
* 8fea96e 210624 | push file.md
* ce0fce5 210624 | created CLI.md
* 6c73087 210624 | created CLI.md

별이랑 | 로 표시된 내용들이 수정된 내용들을 보여준다.
```

- $ git log 로 변경사항 알아보기 

```bash
iseojo@ISEOJO0F5E MINGW64 //Mac/Home/Desktop/TIL_iseo (master)
$ git log
Cygwin WARNING:
  Couldn't compute FAST_CWD pointer.  This typically occurs if you're using
  an older Cygwin version on a newer Windows.  Please update to the latest
  available Cygwin version from https://cygwin.com/.  If the problem persists,
  please see https://cygwin.com/problems.html

commit f164dd13dd18af84767b1a3b4abfd461af57d1fd (HEAD -> master)
Merge: 57ad14e 4b42b8d
Author: joiseo <joiseo.dev@gmail.com>
Date:   Fri Jun 25 11:37:31 2021 +0900

    Merge branch 'login'

commit 57ad14e6395d72a9288604c524362f043e2ddd3a
Author: joiseo <joiseo.dev@gmail.com>
Date:   Fri Jun 25 11:23:26 2021 +0900

    create master.py

```



### 브랜치 삭제

```bash
$ git branch -d 브랜치명
```

## 브랜치 강제 삭제

```bash
$ git branch -D 브랜치명
```

- merge가 되지 않은 브랜치는 강제로 삭제해야함.



## 3가지 병합 상황

### 1. fast-forward

" 다른 브랜치를 생성한 후, master브랜치(상황에 따라 다름)에 변경 사항이 없을 때"

### 2. 3-way Merge

"현재브랜치(master)가 가리키는 커밋이 Merge할 브랜치의 조상이 아니라면(독자적인 상황을  가리키는)" git은 현재 브랜치와 머지할 브랜치의 커밋 2개와 두 브랜치의 공통조상 하나를 사용한다."

1. 새로운 브랜치 signup 생성
2. signup 브랜치에서 signup.py 생성
   - git add,commit 잊지말기
3. master 브랜치에서 new folder와 new.py 파일생성
   - git add,commit 잊지말기

4. master 브랜치와 signup 브랜치 병합

5. signup 브랜치 삭제



### Merge Conflict

" 두 개의 브랜치가 동일한 파일의 동일한 위치를 수정하고 merge 하려고 할 깨 발생하는 현상"

단, 동일 파일을 수정했다고 하더라도 서로 다른 영역을 수정한다면 merge conflict는 발생하지 않는다."

- git이 자동으로 병합하지 못하는 상황

1. 새로운 브랜치 hotfix 생성

```bash
$ git branch hotfix 
$ git checkout hotfix
# $ git checkout -b hotfix
```



2. hotfix브랜치에서 b.txt에 새로운 내용 입력

- git add, commit

```bash
$ git add. or b.txt
$ git commit -m "message"
```



3. master 브랜치에서 b.txt에 새로운 내용 입력

- git add, commit

```bash
$ git add. or b.txt
$ git commit -m "message"
```



4. master 브랜치와 hotfix 브랜치 병합



### q

- 병합한 후에 다 볼 수 가 없어서 끝까지 내려오다 end로 끝나면 q를 누르면 나올 수 있다.