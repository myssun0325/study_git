# GIT

## 저장소 만들기
> git init

## git이 관리할 대상 파일 등록
> git add 파일이름
- 상태확인하기
    > git status

## 버전에 포함될 만든사람에 대한 정보 설정(1회)
> git config --global user.name "자신의 닉네임"
> git config --global user.email "자신의 이메일"
이후
> git commit 을 치고 커밋 메시지를 입력

## stage area
- stage : commit 대기한 파일들
- repository : commit의 결과가 저장되는 곳

## 변경사항 확인하기
> git log
- commit간의 차이 출력하기
    > git log -p
> git diff commit번호1 commit번호2
> git diff

## 과거의 버전으로 돌아가기
- `reset`과 `revert`
- reset해서 원하는 commit으로 돌아가기 (그 commit 이후 버전은 삭제)
    > git reset [돌아가려는commit번호] --hard
    - 실제로는 삭제된것이 아니다. 남아있다.
- 나중에 원격으로 공유할 때는 reset작업을 하지 말것
- revert : commit을 취소하면서 새로운 버전을 생성한다.

## Branch 만들기
- Branch 확인
    > git branch
- Branch 생성하기
    > git branch [branch명]
- branch를 생성한 시점에서의 branch상태를 그대로 복사한다.
- branch checkout(전환) 하기
    > git checkout [branch명]
- branch 삭제하기
    > git branch -d
- 병합하지 않은 브랜치 강제 삭제하기
    > git branch -D
- 브랜치 생성 후 전환까지 한꺼번에
    > git checkout -b "생성하고 전환할 브랜치 이름"

## Branch 정보확인
- branch 차이 확인하기
    > git log --branches --decorate
- graph 확인하기(master와 branch가 서로 다른 commit상태일 때 확인하기 좋다)
    > git log --branches --decorate --graph [--oneline]
- branch 간 차이 확인하기
    > git log "비교할 브랜치명1".."비교할 브랜치명2"
- 브랜치 간의 코드까지 비교할 때 (위에서 -p옵션을 붙이거나.)
    > git diff "비교할 브랜치명1".."비교할 브랜치명2"

## Branch 병합하기
- branch에서 master로 병합하기
    - 생성브랜치 => master로 병합을 원할 경우 : master로 checkout 한 뒤에 `git merge 브랜치명`
- merge후 commit은 두 개의 부모commit을 갖는다. 1. 원래 마스터의 commit 2. 브랜치가 작업했던 commit
- master -> branch
    - git checkout "브랜치" -> git merge master

## Fast forward
- fast forward는 branch 작업 후 master branch에서 따로 변경사항이 없으므로 merge후 따로 commit을 생성하지 않는다.
- fast forward가 아닐 경우 merge commit을 자동으로 생성한다.
참조 연습 링크 : https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%B8%8C%EB%9E%9C%EC%B9%98%EC%99%80-Merge-%EC%9D%98-%EA%B8%B0%EC%B4%88

## merge시 conflict발생 시!
- <<<<HEAD부터 ====사이의 구간이 현제 체크 아웃된 파일의 내용
- =====부터 >>>브랜치명 구간이 병합하려는 대상의 코드 내용
- 이 정보를 참고로해서 두개의 코드를 병합한 후 특수 기호들을 제거 해주면된다.
https://opentutorials.org/course/2708/15275

## stash
- 다른 브랜치로 checkout을 해야하는데 현재 브랜치에서 작업이 끝나지 않아서 commit을 하기 애매할 때 작업중이던 파일을 임시로 저장해두고 현재 브랜치의 상태를 마지막 커밋의 상태로 초기화.
- git stash를 하게 되면 git stash list 에 들어가면서 현재 작업을 감출 수 있다.(git status시 내용이 나타나지 않는다.)
- git stash apply를 통해 다시 복원할 수 있다. git stash drop을 통해 리스트에서 지울 수있다. -> 둘이 한꺼번에 : `git stash pop`
- stash는 적어도 add를 해야한다. (버전관리에 등록이 된 파일에 한해서 stash가 된다.)


## 원격저장소
- 2가지 역할 : 백업과 협업
- git init --bare 별명 사용할위치
- 원격 저장소에 push하기(origin에 master를!) : git push origin master
