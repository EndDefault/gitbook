#버전
깃에서 버전이란 문서를 수정하고 저장할 때마다 생기는 것
버전을 만든 시간과 수정 내용까지 기록할 수 있는 것이 바로 깃과 같은 버전관리 시스템

#스테이지에 변경 사항 올리기
$ git add [파일 이름]
작업 트리에서 파일을 만들거나 수정했다면 스테이지에 추가
깃에게 버전 만들 준비를 하라고 알려 주는 것을 스테이징(staging)또는 스테이지에 올린다라고 표현

$ git add .
작업 트리에 있는 수정 파일들을 스테이지에 한꺼번에 올릴 수 있음

#깃 기록 확인
$ git log
## 한줄로 간단하게 표시
$ git log --oneline
## 다른 브랜치의 최신 커밋을 알 수 있음
$ git log --oneline --branches
- 원래는 표시가 되지만 가지가 갈라질 때 다른 가지에 최신 커밋의 브런치를 볼 수 있게 해준다.
## 그래프 형태로 보는법
$ git log --oneline --branches --graph
## 브랜치 간의 차이점
$ git log [브랜치1]..[브랜치2]
- [브랜치1]에 없고 [브랜치2]에만 아있는 브런치를 보여준다.
##모든 로그 출력
$ git log --all
최신 뿐만 아니라 모든 로그를 출력

$ git log --stat
가장 최근 커밋부터 수넛대로 커밋 메시지와 관련 파일이 나열됩니다.

#깃 생성
$ git init

#깃 상태 확인
$ git status

#스테이징한 파일 커밋하기
$ git commit -m [커밋 메세지]
스테이징 영역에 있다면 버전을 만들 수 있음
커밋(commit)한다 : 버전을 만드는 것

# 스테이징과 커밋 한꺼번에 처리하기
$ git commit -am [커밋 메세지]
##한 번이라도 커밋한 적이 있는 파일을 다시 커밋할때 사용 가능

#방금 커밋한 메시지 수정
$ git commit --amend

# 되돌리기
## 작업 트리에서 수정한 파일 되돌리기
$git restore [수정된 파일]

## 스테이징 되돌리기
$ git restore --staged
- add한 정보를 다시 돌린다.

##되돌리기 팁
$ git status 를 입력한 경우 Changes not staged for commit:에 정보를 확인할 수 있다.

#커밋 되돌리기
## 방금 커밋 되돌리기
$ git reset HEAD^

## 원하는 위치로 커밋
$ git reset --hard [커밋 해시]

#변경 이력 취소

#변경 사항 확인하기 
$ git diff

#tracked 파일과 untracked 파일
$git status

#브랜치
##확인
$git branch
##생성
$git branch [브랜치 이름]

##부가 설명
- log를 통해소 현재 버전에 브랜치확인 가능(HEAD -> 브랜치들)
- HEAD옆 브랜치들이 모든 버전을 고유하고 있음

##브랜치 전환
$ git switch [생성된 브랜치 이름]

##브랜치 합병
$ git merge [합병할 브랜치]
- 현재 브랜치에 [합병할 브랜치]를 가져와 붙인다
- 이때 "Merge branch '[합병할 브랜치 이름]'"이렇게 커밋된다

##브랜치 삭제
$ git branch -d [브랜치 이름]
- 삭제되더라도 다시 만들면 이전 작업이 그대로 만들어짐

Changes not staged for commit:
	modified: [내용 변경 파일]
	new file: [스테이징된 파일]
Untracked files:
	[새로 만든 파일]

#파일 상태
## M 
M = modifie '수정한다.'
## U
U = Unmerged
## A
Added 

#설정변경
## 터미널 창 -> 페이지로 변경 가능
$ git config --global core.editor "code --wait"



#정보

##2줄 한꺼번에 정의 
$ [1번째 문장]; [2번째 문장]
- ;(세미컬론)을 이용하여 2 문장을 한번에 사용 가능

##merge 충돌
112쪽

##cherry-pick 병합
117쪽
cherry-pick은 main 브랜치와 topic 브랜치를 합치지만 브랜치 전체가 아니라 topic 중에서
특정 버전의 변경 내용만 합침
$ git cherry-pick [복사한_커밋_해시]

#git-hub
136쪽

##깃 허브 저장소에 연결하기
$ git remote add origin [깃허브 주소]

##깃 허브 연결 확인
$ git remote -v

##깃 허브 
$ git push -u origin main
원격 저장소의 main브런치로 푸시

##깃 허브에 넣기
$ git push

##깃 허브에서 내용 추가
p147

##깃 허브 내용 내려받기
$ git pull origin main

#SSH 원격 접속하기
p154 - 나중에 확인

#
##tocuh
파일생성