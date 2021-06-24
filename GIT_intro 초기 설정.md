# GIT 초기 설정

커밋 작성자 설정

```bash
# 명령을 시키고자 하는 주체
# git아, 전역 설정중, 유저의 email을 설정 할거야.
$ git config --global user.email joiseo.dev@gmail.com
# git아, 전역 설정중, 유저의 name을 설정 할거야.
$ git config --global user.name joiseo
```

ctrl+l 을 누르면 깃허브 창이 깔끔해진다!

- 커밋을 작성하는 사람이 누구인지 알아야하기 때문에

- 지정된 설정을 확인하는 것도 좋은 방법

- ```bash
  # git아 현재 전역에 설정된 설정 목록 보여줘
  $ git config --global -l
  # git congig --global --list(l)
  ```

# Git Basic

```bash
$ git init
```

- 폴더에 git 저장소를 초기화하면,

  - .git이라는 숨김폴더가 생기고
  - bash에는 (master)라는 표시가 생성된다.

  

  

- 주의 사항
  - .git폴더를 직접적으로 수정하는 일은 없을 것이다.
  - 이미 git으로 관리하고 있는 (bash창에 master가 표기되어 있는 폴더 내에서는 절대 git init하지 말 것)



# status

```bash
# git아 너가 관리중인 폴더의 상태 보여줘
$ git status
```

# add

```bash
$ git add 파일명
$ git add . # 현재 폴더(디렉토리)
$ git add a.txt # 특정 파일
$ git add directory_name/ #특정 폴더가 가진 모든 파일
```

- working directory 상태의 파일을 staging area상태로 변경

- 팁으로 자동완성 기능은 스펠링쓰고 텝(tap)키를 쓰면 쓸 수 있다

- touch는 파일을 새로 만들어주는 행위 $ touch a.txt

- add. 파일을 수정, 삭제, 저장 등 모든 변경 사항들을 저장하는 것.

- 커밋이라는 행위를 하기 전에 커밋을 위한 파일 및 폴더들을 추가하는 명령어

  

  

# commit

```bash
# git아, commit 할건데 -메세지는 "이걸로 해줘"
$git commit -m "commit message"
# git commit -m "210624 | created CLI.md"
```

- 커밋을 통해 하나의 버전으로 기록 됨

- 커밋 메세지는 현재 변경사항들을 잘 나타낼 수 있도록 작성하는 것을 권장

- 컨트롤+c는 모든걸 빠져나옴

- 커밋 목록은 git log 를 통해서 확인할 수 있음

  - commit 6c73087d0bdb782e97f5ae828f909c323e77ee7d (HEAD -> master)
    Author: joiseo <joiseo.dev@gmail.com>
    Date:   Thu Jun 24 16:27:41 2021 +0900

      210624 | created CLI.md

```bash
$ git log  --oneline
```

