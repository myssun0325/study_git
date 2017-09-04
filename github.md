# Github

## git 소스코드를 지역저장소로 가져오기 (원격저장소 복제하기)
> git clone 주소 [가져와서 저장할 폴더 이름(생략가능)]

- log 거꾸로 출력하기 : git log --reverse
- git checkout 커밋id

## 원격 저장소 만들기 (Github)
- 2가지 케이스
    1. 원격저장소를 만들고 -> 로컬로
    2. 이미 있는 로컬 저장소 -> 원격저장소

- 이미 있는 로컬 저장소 -> 원격저장소
    - github에서 만들고나서 git remote add origin "원격저장소주소"
    - 로컬저장소를 기준으로 push (로컬 => 원격)
    - git push -u origin master에서 `-u`의 옵션은 다음부턴 git push만해도 origin에서 master로

- 원격 저장소 -> 로컬 저장소
    - git clone [주소] [저장할 경로]
    - git remote -v로 확인해보면 clone하면 기본적으로 origin이 부여되는걸 알 수 있다.

## 원격저장소와 지역 저장소의 동기화 (Github)
- `git pull` : 원격 저장소 => 로컬 저장소
- git_home, git_office라는 두개의 다른 로컬 저장소와 원격저장소가 있을 때 (git_home과 git_office는 같은 원격저장소를 clone했음)
- git_home에서 작업한 것을 커밋 후 push 한 후에 git_office라는 로컬저장소에서 다시 작업할 때 `git pull`을 통해 원격저장소의 내용을 가져와 git_office라는 로컬저장소에 갱신한다.
