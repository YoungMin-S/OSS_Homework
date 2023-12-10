# OSS_Homework
## 배운 내용들 정리해서 올렸습니다. commit들이 있으니 어떤 내용을 사용하였는지는 commit을 확인하시면 됩니다. 
### status 명령어
변경사항을 확인하는 명령어
#### 옵션 
+ -s : 간략하게 보여준다.
### add 명령어 
Staging area로 이동 
+ 주로 'git add .'을 사용해서 변경사항을 저장한다.
### commit 명령어
Repository로 이동 
#### 옵션
+ -m : 메시지와 함께 작성
+ -am : add와 commit을 한번에 하는 방법이다 (untracked 파일이 없을 때 한정이다.)
+ --amend : 커밋 메시지 변경
  + git commit --amend -m '메시지' : 커밋 메시지 한줄로 변경  
### Git의 HEAD
현재 속한 브랜치의 가장 최신 커밋이다.
+ ^ 또는 ~: 갯수만큼 이전으로 이동이 가능하다
  + git checkout HEAD^^^^ , git checkout HEAD~5
+ git checkout - : 한 단계 되돌리기
### log 명령어 
커밋 이력 확인
#### 옵션
+ -p : 변경사항 함께 보기
+ git log -(갯수) : 최근 n개 커밋 보기
+ --stat : 통계와 함께 보기
+ --oneline : 한줄로 보기 
+ -S (검색어) : 변경사항 내 단어 검색
+ --grep (검색어) : 커밋 메시지로 검색
### diff 명령어 
작업 디렉토리의 변경사항 확인
#### 옵션 
+ --name-only : 파일명만 확인
+ --staged,--cached : 스테이지의 확인
#### 사용
+ git diff (커밋해쉬1) (커밋해쉬2) : 커밋간의 차이 확인
  + 커밋 해시 또는 HEAD번호로 가능하다
  + 현재 커밋과 비교하려면 이전 커밋만 명시한다
 ### resotre 
특정 파일을 지정된 상태로 복구
#### 사용 
+ git restore (파일명) : 작업 디렉토리의 특정 파일 복구
  + 파일명 자리에 . : 모든 파일 복구
+ git restore --staged (파일명) : 변경상태를 스테이지에서 작업 디렉토리로 돌려 놓기
+ git restore --source=(HEAD혹은 해쉬) 파일명 : 파일을 특정 커밋의 상태로 되돌리기
### Git Tag
특정 시점을 키워드로 저장하고 싶을 때 
커밋에 버전 정보를 붙이고자 할 때 사용 
#### 사용 
+ git tag v2.0.0 : 마지막 커밋에 v2.0.0 태그 달기
+ git tag : 현존하는 태그 확인
+ git show v2.0.0 : 원하는 태그의 내용 확인
+ git tag -d v2.0.0 : 태그 삭제
+ git tag v2.0.0 -m 'test' : 태그와 메시지 달기
  + -m 태그가 -a 태그 암시
+ git tag 태그명 커밋해시 -m 메시지 : 원하는 커밋에 태그 달기
+ ![image](https://github.com/YoungMin-S/OSS_Homework/assets/129874185/abc71ea3-1bbe-40e4-a92b-38372dcce965)


### branch
다른 차원
프로젝트를 하나 이상의 모습으로 관리해야 할 때 사용된다 
#### 사용
+ git branch [브랜치명] : 브랜치명에 따라 브랜치 생성
+ git branch : 브랜치 목록 확인
+ git switch [브랜치명] : 브랜치명을 가진 브랜치로 이동
+ git switch -c [브랜치명] : 브랜치명을 가진 브랜치를 생성하고 이동
+ git branch -d [브랜치명] : 브랜치 삭제
  + -D : 강제 삭제
+ git branch -m (기존브랜치명) (새 브랜치명) : 브랜치 이름 변경
+ ![image](https://github.com/YoungMin-S/OSS_Homework/assets/129874185/876e02e8-0ec0-4744-bfaf-18397241769b)

### 원격 저장소 복제연동 
+ git clone (원격 저장소 주소)
### 원격으로 커밋 올리기 (push)
+ git push
### 원격의 커밋 당겨오기 (pull) 
+ git pull
#### 주의 사항
![image](https://github.com/YoungMin-S/OSS_Homework/assets/129874185/59c851eb-5b0b-4609-a1f1-48133b59c14f)
pull할 것 이 있을 때 push를 하면 문제가 발생할 수 있다. 
+ git pull --no-rebase -> merge 방식
+ git pull --rebase -> rebase 방식
### fetch 
+ pull과 fetch의 차이
  + pull : 원격 저장소의 최신 커밋을 로컬로 가져와 merge혹은 rebase
  + fetch : 원격 저장소의 최신 커밋을 로컬로 가져오기만 한다. -> merge를 해줘야 한다.
### stash
임시저장 해주는 것이다. 
stash 전 
![image](https://github.com/YoungMin-S/OSS_Homework/assets/129874185/cb474eec-dfd3-407c-9ec6-a1a2a2eb2301)
stash 후 
![image](https://github.com/YoungMin-S/OSS_Homework/assets/129874185/0bd4e0d6-2caa-4b1a-b74f-554a0fd86af4)
소스트리에서 저장된 것을 확인이 가능하다.
 ![image](https://github.com/YoungMin-S/OSS_Homework/assets/129874185/9b897fc2-ec54-46e3-9917-2900452c3e48)
#### 사용
+ git stash : 저장해두기
  + git stash save와 동일
+ git stash pop : 원하는 시점, 브랜치에 다시 적용
+ git stash -m '메시지' : 메시지와 함께 스태시
+ git stash list : 스태시 목록 확인
  + 리스트 상의 번호로 apply,drop,pop 가능
+ git stash apply : stash한 마지막 항목 적용 -> git stash apply stash@{1}로 사용 가능
+ git stash drop : stash한 마지막 항목 삭제 -> git stash apply stash@{1}로 사용 가능
+ git stash clear : 모든 stash 목록 삭제
+ git stash show : 커밋 자료와 최신 stash 항목간의 차이
### 브랜치 병합(merge) 
+ git merge (병합할 브랜치)
+ git merge --no-ff (브랜치명) -> fastforward를 하지 않겠다
+ git merge --squash (대상 브랜치) : 대상 브랜치의 마디들을 하나로 묶어 현재 브랜치로 가져오기 
![image](https://github.com/YoungMin-S/OSS_Homework/assets/129874185/33f46a32-7ffb-4f47-99a0-77bdf6b840c6)\
+ fastforward : 두 브랜치가 공통 커밋을 조상으로 갖고 있는데 한쪽 브랜치에만 이후에 커밋이 있을 때 그 상태에서 병합할 때 사용
+ 3-wqy merge : 양쪽 브랜치 둘다 커밋된 마디가 하나 이상 있는 상태에서 merge하는 경우
+ ![image](https://github.com/YoungMin-S/OSS_Homework/assets/129874185/84ec048f-09f0-48e9-86d2-30aa2cffd414)

+ git merge --abort : 당장 충돌 해결이 어려울 경우 merge 중단 
### 브랜치 병합(rebase)
merge와는 반대로
+ git rebase (병합이 될 브랜치)
  + 그 후 merge를 이용하여 fastforward
### git rebase -i (대상 이전 커밋)
HEAD로도 가능 
+ p : 커밋 그대로 두기
+ r : 커밋 메시지 변경
+ e : 수정을 위해 정지
+ d : 커밋 삭제
+ s : 이전 커밋에 합치기
### git reset 
해당 해쉬로 가는 법 
+ git reset --hard (돌아갈 해쉬) 
#### 옵션
+ --soft : repository -> staging area로 이동
+ --mixed : repository -> working directory로 이동
+ --hard : 수정사항 완전히 삭제
### git revert 
과거의 커밋 되돌리기
+ git revert (되돌릴 커밋 해쉬)
![image](https://github.com/YoungMin-S/OSS_Homework/assets/129874185/00f7157d-596a-487d-92c0-c1e543ece0d2)
#### reset과 revert 
+ reset : 원하는 시점으로 돌아간 뒤 이후 내역들을 삭제
+ revert : 되돌리기 원하는 시점의 커밋을 거꾸로 실행 
