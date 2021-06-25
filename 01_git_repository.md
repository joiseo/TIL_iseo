# 원격저장소 (remote repository)

## 기본 설정

1. 로컬 git 저장소 준비 
2. github reposiory 생성
3.  Repository default branch 변경



## 명령어

### 원격저장소 주소 추가

```bash
# git아, 원격 저장소 주소 origin 이라는 이름으로 추가 할건데, 
# 주소는 이거야.
$ git remote add origin https://github.com/joiseo/TIL_IS.git

```



### 원격 저장소 목록 보기

```bash
$ git remote -v
```

### 원격 저장소 삭제

```bash
$ git remote rm origin
```



### 원격 저장소에 업로드 (push)

```bash
# git아 업로드 할건데 origin이라는 이름으로 저장해둔 원격 저장소에 master 브랜치의 commit 내역들을 업로드할거야.
$ git push -u origin master
```

- commit 내역이 없으면 업로드 불가능



//////// 잠깐 /////!!!

```bash
$ git --version
```

git의 version을  알아볼 때 쓰임

# clone

- 원격저장소 내용 전체 복제

```bash
$ git clone {원격저장소 url}
```

- 주의사항
- 이미 git init이 되어있음

## pull

- 원격저장소의 변경사항을 받아온다(업데이트)

```bash
$ git pull origin master
```

