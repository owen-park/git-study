# Git
- 개념 정리

    |개념|명령어|설명|
    |:---:|:---|:---|
    |add|```git add 파일명```|변경된 파일을 ***스테이징 영역***에 추가<br>※ ***스테이징 영역*** : 커밋으로 확정 짓기 전 변경사항을 임시로 모아두는 곳|
    |commit|[기본]<br>```git commit -m "커밋 메시지"```<hr>[메시지 여러 줄 이력]<br>```git commit -m "커밋 메시지" -m "커밋 메시지"```<hr>[add (tracked & modified 파일 전체) + commit]<br>```git commit -a -m "커밋 메시지"```<hr>[add (tracked & modified 파일 선택) + commit]<br>```git commit -p -m "커밋 메시지"```<hr>[마지막 커밋을 날리고 새로운 커밋]<br>```git commit --amend -m "커밋 메시지"```<hr>[author 정보 변경하여 커밋]```git commit --author="이름 <이메일>" -m "커밋 메시지"```|스테이징 영역에 추가된 변경사항을 실제로 저장소에 기록<br>※ Commit은 단순히 파일의 변경사항을 기록하는 것 이상의 의미를 가짐<br>&emsp;프로젝트의 ***히스토리***를 만들어가는 과정이며 팀원 간의 ***소통 수단***이 됨|
    |checkout|[특정 브랜치로 전환]<br>```git checkout 브랜치명```<hr>[특정 브랜치 생성 후 바로 전환]<br>```git checkout -b 브랜치명```<hr>[특정 베이스 브랜치에서 파생 브랜치를 생성 후 바로 전환]<br>```git checkout -b 브랜치명 베이스브랜치명```<hr>[모든 변경사항 취소]<br>```git checkout .```<hr>[변경사항 커밋 전으로 복원]<br>```git checkout -- 파일명```<hr>[특정 커밋 버전으로 전환]<br>```git checkout 커밋해시값```|* 브랜치 또는 커밋을 전환함 (switch)<br>* 내용 되돌리기 (restore)|
    |HEAD|[한 단계 위의 커밋]<br>```HEAD^```<br>```HEAD~1```<hr>[두 단계 위의 커밋]<br>```HEAD^^```<br>```HEAD~2```|* 특정 브랜치의 마지막 커밋<br>* 현재 작업중인 커밋<br>* 상대참조<br>&emsp;1. ^ : 한번에 한 커밋 위로 올라감<br>&emsp;2. ~<num> : 한번에 여러 커밋 위로 올라감|
    |stash|[임시 저장]<br>```git stash```<hr>[stash 목록 확인]<br>```git stash list```<hr>[가장 최근 stash 불러와 적용]<br>```git statsh apply```<hr>[특정 stash 불러와 적용]<br>```git stash apply 스태시명```<hr>[staged 상태까지 복원하여 stash 불러와 적용]```git stash apply --index```<hr>[가장 최근 stash 제거]<br>```git stash drop```<hr>[특정 stash 제거]<br>```git stash drop 스태시명```|변경내용을 일시적으로 기록해두고 나중에 다시 불러올 수 있는 기능|
    |merge|```git checkout main; git merge feature-branch```|* 2개 이상의 개발 히스토리를 하나로 합치는 작업<br>* merge를 하게 되면 각각의 개발자가 작업한 히스토리가 모두 보존됨(히스토리가 시계열로 남음)|
    |rebase|```git rebase main feature-branch```|* 브랜치의 베이스를 재설정하여 다시 커밋을 재적용하는 작업<br>* 기존 커밋이 새로운 해시값을 가진 커밋으로 다시 처리되어서 히스토리가 깔끔해짐<br>* 리베이스 규칙<Br>&emsp;1. 원격 저장소에 올라간 커밋은 리베이스 하지 말아야 함<br>&emsp;2. 리베이스 전에 리베이스 하려는 브랜치 끝에서 백업 브랜치를 만들기|
    |pull|```git pull```|최신커밋 가져오기(fetch) + 병합(merge)|
    |fetch|```git fetch```|최신커밋 가져오기|
    |push|```git push origin 브랜치명```|로컬 브랜치의 변경내용을 원격 저장소로 밀어넣음|
    |tag|[생성]<br>```git tag 태그명```<hr>[특정 커밋 태그 지정]<br>```git tag 태그명 커밋해시값```<hr>[tag 목록 조회]<br>```git tag```<hr>[tag 삭제]<br>```git tag -d 태그명```<hr>[tag 확인]<br>```git tag -n```<hr>[tag 푸시]<br>```git push origin 태그명```<hr>[원격 저장소에 올라간 tag 삭제]<br>```git push --delete origin 태그명```|* 특정 커밋에 레이블을 지정하여 태그를 붙이는 기능<br>* 특정 커밋의 버전을 명시할 수 있음|
    |diff|[커밋 전 스테이징 영역 변경내용 보기]<br>```git diff --cached```<hr>[워킹디렉토리 변경내용 보기]<br>```git diff```<hr>[워킹디렉토리 & 스테이징 영역 변경내용 동시에 보기]<br>```git diff HEAD```<hr>[커밋 간의 차이 보기(예시)]<br>```git diff HEAD HEAD^```<hr>[브랜치 간의 차이 보기]<br>```git diff 브랜치명 브랜치명```<hr>[특정 접두어가 들어가는 파일만 비교]<br>```git diff --name-only src/pages/*```|커밋들 간의 차이점이나 워킹트리와 커밋사이의 차이점을 보여줌|
    |reset|[특정 커밋으로 원복]<br>```git reset 커밋해시값```<hr>[변경사항도 제거하면서 특정 커밋으로 원복]<br>```git reset --hard 커밋해시값```|* 특정 커밋으로 돌아가며, 돌아가고자 하는 커밋과 현재 커밋 사이의 모든 커밋이 제거됨<br>* 변경내용들은 워킹디렉토리에 남겨둘 수 있음(옵션을 주어 지울 수도 있음)<br>※ 협업환경에서는 사용하지 않음|
    |revert|[특정 커밋 제거(바로 적용)]<br>```git revert 커밋해시값```<hr>[특정 커밋을 제거하는 변경사항을 스테이징 영역에만 올림]<br>```git revert --no-commit 커밋해시값```<br>```git commit -m "커밋 메시지"```|* 특정 커밋으로 돌아가지만, 과거 커밋과 현재 커밋 사이의 커밋들을 제거하지 않음<br>* 기존 내용을 삭제하는 변경사항을 가진 커밋을 새로 올림|
    |cherry-pick|[특정 커밋 가져오기]<br>```git cherry-pick 커밋해시값```<hr>[연속적인 커밋 가져오기]<br>```git cherry-pick 시작커밋해시값..종료커밋해시값```<hr>[체리픽 중단]<br>```git cherry-pick --abort```|다른 브랜치의 커밋을 내 브랜치에 적용시키는 기능<br>※ 체리픽 충돌 해결방법<br>&emsp;1. 충돌난 코드 수정<br>&emsp;2. git add 수정파일<br>&emsp;3. git cherry-pick --continue|
    |log|[기본]<br>```git log```<hr>[커밋ID와 타이틀 메시지만 조회]<br>```git log --oneline```<hr>[모든 브랜치 커밋 이력 조회]<br>```git log --oneline --decorate --graph --all```<hr>[특정 파일 변경 커밋 조회]<br>```git log --index.html```<hr>[diff 조회]<br>```git log -p -<num>```<hr>[커밋 통계 정보 조회]<br>```git log --stat```|커밋 이력 조회|
    |reflog|```git reflog```|HEAD의 업데이트 기록을 보여줌|
    |clean|[모든 Untracked 디렉토리/파일 삭제]<br>```git clean -ffdx```|Untracked 파일 삭제 기능|