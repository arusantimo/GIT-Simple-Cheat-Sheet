# GIT-Simple-Cheat-Sheet
자주 쓰는 git 명령어와 설명

git을 설치하면 git init으로 깃을 시작한다.

# 환경설정

## 계정 설정
로컬저장소 사용자 정보 설정 자신의 깃저장소 서비스(github, bitbucket)의 계정으로 등록하는 것이 좋다.
```
$ git config --global user.name "[name]"
$ git config --global user.email "[email address]"
```
## ssh key 등록
자신의 ssh키 등록 자신의 .ssh 디렉토리에 있는 ssh-rsa파일을 깃헙 계정 셋팅에 들어가 ssh key에 등록한다.

# 저장소 생성

## 새로운 저장소 생성
```
$ git init [project-name]
```
## 저장소 서비스 (github)에서 프로젝트 다운로드
```
$ git clone [url]
```

# 코드 업로드

```
$ git add [file] //저장소에 추가 모든 파일은 --all
$ git commit -m “메시지” // 로컬 커밋
$ git push // 원격 저장소 origin으로 Push
```

# 코드 받기
```
$ git fetch //원격 저장소 origin에서 모든 branch 코드 받아오기 merge는 되지 않음
$ git pull //원격 저장소에서 현재 branch 코드 받아오고 merge한다.
```

# 코드 비교 꺠짐 수정

```
$ git status // 현재 작업중인 branch 상태를 확인한다.
$ git diff --stat --color [commit, branch] [commit, branch]// 두 브랜치또는 커밋을 비교
```

# log관련

```
$ git log [file] //특정 파일또는 작업중인 브랜치의 커밋 로그를 보여준다.
$ git log --author="사용자이름" //특정 사용자로 커밋 로그를 검색한다.
```

# 현재 작업 브랜치 히스토리 변경

```
$ git checkout [commit_id, branch_name] // 특정 브랜치나 커밋 히스토리 시점으로 이동
```

# 임시저장

```
$ git stash //임시로 현재 커밋하지 않고 트래킹된 파일들을 저장.
$ git stash pop //가장 최근에 숨겨진 파일을 복원한다.
$ git stash list //모든 숨겨진 변경 사항들의 리스트를 보여준다.
$ git stash drop //가장 최근에 숨겨진 변경 사항을 버힌다.
```

# rebase
```
$ git rebase -i HEAD~갯수 //원하는 갯수만큼 커밋로그를 합친다.
$ git rebase -i [branch] //특정 branch에 현제 브런치의 히스토리의 뿌리를 바꿔서 최신의 히스토리로 유지할수 있게 해준다. (rebase할 branch는 미리 최신화 시킨다.)
```

# 태그
```
$ git tag -l // 태그의 목록을 보여준다.
$ git tag -a [tagname] [commit] -m “태그 설명” // commit을 지정하지 않으면 현재 커밋.
$ git tag -d [tagname] // 태그 삭제
$ git push --tags // 태그 전체를 리모트로 푸시
$ git push origin [tagname] // 특정 태그를 리모트로 푸시 삭제
```

# git flow

```
$ brew install git-flow-avh //설치
$ git flow init //초기 설정 config설정은 일단 그냥 enter들 게속 놀러 스킵한다.
 > master / develop의 두개의 기본적인 브랜치가 생성된다.
$ git flow feature start [MYFEATURE] // 새기능 시작한다. > develop에서 생성된다.
$ git flow feature finish [MYFEATURE] // 기능을 완료한다. (완료 전에 깃헙 PR 코드리뷰를 하는 것이 좋다.) > develop에 merge된다.
$ git flow release start [RELEASE] // 배포준비를 시작한다. > develop에서 생성된다.
$ git flow release finish [RELEASE] // 배포준비 작업을 완료한다. (git push --tag를 해준다.) > develop과 master에 merge된다.
$ git flow hotfix start [HOTFIX] //문제가 생겨 즉각 내용을 수정해야 하는 상황에서 사용 > master에서 생성된다.
$ git flow hotfix finish [VERSION] //문제를 해결하고 긴급패로를 준비한다. > develop과 master에 merge된다.
```

# gir branch

```
$ git branch -D [Branch-name] //git branch 삭제 (d => 삭제 d=>강제삭제)
```

모든 배포는 master 브랜치로만 이루어 진다.
