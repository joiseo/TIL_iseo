## undoing

> 원 상태로 되돌리기 (''>+스페이스' 누르면 만들어진다.')

#### 1. 폴더 undoing 생성

#### 2. undoing폴더 안으로 작업 위치변경

#### 3. u.txt, doing.txt 생성



## 1. 파일 상태를 unstage로 변경하기

#### 첫번째

```bash
$ git rm --cached {파일명}
```

- 따로따로 커밋하려고 했는데 실수로 전부 git add. 해버렸을 때
- 그리고, 최초로 add를 한 상황(해당 파일들에 대한 commit이 없는 경우)

#### 두 번째

1. un.txt doing.txt 둘 다 commit 남기기
2. 두 파일 모두 수정사항 만들기
3. 실수로 git add. 하기

```bash
$ git resore --staged <file> # un.txt 
```

////// 오류가 뜰 때

```bash
$ git status
On branch master
Your branch is ahead of 'origin/master' by 6 commits.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   ../b.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ./

no changes added to commit (use "git add" and/or "git commit -a")
```

```bash
On branch master
Your branch is ahead of 'origin/master' by 6 commits.
  (use "git push" to publish your local commits)
  
  #이건 마스터 브랜치에 커밋이 쌓였는데 레포지토리에 반영이 안됐다 라는 의미
```



```bash
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   ../b.txt
```

이 부분은 한번 커밋한적 있는 b.txt가 수정되었는데 add 되지 않았다 

```bash
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ./
```

여기는 새로만든 폴더에 한번도 커밋된적 없는 새로운 수정 사항이 존재한다



## 2. Modified 파일 되돌리기

- commit기록은 남아있고, 새롭게 수정한 다음 아직 add하지 않은 working directory에 존재하는 파일의 수정사항을 되돌린다.

- ```bash
  $ git resotr {파일명}
  ```

- 주의사항

- 수정 한 내역 전부를 과거로 돌리는 것이기 때문에 수정한 내용이 사라진다.

- 절대 복원 불가능

- 진짜진짜 수정한 내용이 마음에 안 들때만 쓴다.

 ////// 상단 폴더로 이동할 때 cd ..(띄어쓰기 유의)  add .(띄어쓰기 유의)

### 3-1 commit Message 수정

> 마지막으로 커밋하고나서 수정한게 없는 상태일 때
>
> (커밋하자마자 바로 명령 실행할 때)
>
> 커밋 메세지만 수정

```bash
$ git commit --amed
```



1. vim 진입
2. 키보드 i 혹은 insert키 입력
   - -- INSERT -- 상태로 전환
3. 수정 하고자 하는 commit message 입력
4. esc키 입력
   - -- INSERT -- 상태 최소
5. :(콜론)wq (저장 후 종료 write quite)

![](\\Mac\Home\Desktop\스크린샷 2021-06-25 오후 3.42.51.png)

### *bash 창에서 커서기준 앞 전부 지우기 : ctrl u

### 3-2 commit할 때 파일을 빼먹었다면...

```bash
$ touch foo.txt bar.txt
$ git add foo.txt
$ git commit -m "foo & bar"

# 실수로 bar.txt를 빼먹고 commit을 한 다음...
$ git add bar.txt
$ git commit --amend

$ git log --oneline
add6145 (HEAD -> master) foo & bar
# 새 커밋을 만드는게 아니라 
# 가장 최신의 커밋을 재작성 하는 것이다.
```

- 내가 빼먹은 bar.txt를 

