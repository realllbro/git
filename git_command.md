# 1. 현재 원격 저장소 확인
git remote -v

# 2. 기존 origin 제거
git remote remove origin

# 3. 내 저장소를 origin으로 추가
git remote add origin https://github.com/내계정/내저장소.git
# 또는 SSH: git remote add origin git@github.com:내계정/내저장소.git

# 4. 푸시 (강제 푸시가 필요한 경우)
git push -u origin main --force
# 또는 master 브랜치인 경우
# git push -u origin master --force


## #git 다운로드
<https://git-scm.com/download/win>

## #git 상태

| untracked | tracked |
|:----------|:----------|
| untracked(추적안됨)| unmodified(수정사항 없음) ,modified(수정함), staged(스테이지됨)   |


1. untracked(추적안됨)

      - 한 번도 커밋되지 않은 파일     

2. modified(수정함) 

      - 최초 커밋 이 후 수정된 파일       

3. staged(스테이지됨)

      - 1,2 상태의 파일을 add 명령어를 통해 스테이지에 올림 

4. unmodified(수정사항 없음)

      - 스테이지된 상태에 파일을 commit 명령어를 통해 하나의 스냅샷 및 버전이 생성되고 

        파일 상태는 unmodified(수정사항 없음) 으로 변경됨       

5. push 명령어로 원격 저장소 업로드     

  

* #### 워킹트리 

  * 일반적인 작업이 일어나는 곳

    워크트리, 워킹 디렉토리, 작업 디렉토리, 작업 폴더 모두 같은 뜻으로 사용됩니다.

    일반적으로 사용자가 파일과 하위 폴더를 만들고 작업 결과물을 저장하는 곳을 Git에서는 워킹트리라고 부릅니다. 

    공식문서에서는 워킹트리를 '커밋을 체크아웃하면 생성되는 파일과 디렉토리' 로 정의하고 있습니다.

    정확하게는 작업 폴더에서 [.git] 폴더(로컬저장소)를 뺀 나머지 부분이 워킹트리입니다.

  

* #### 로컬저장소

  * .git폴더, 커밋은 여기에 들어 잇다.

    Git init 명령으로 생성되는 [.git] 폴더가 로컬저장소입니다. 커밋, 커밋을 구성하는 객체, 

    스테이지가 모두 이 폴더에 저장됩니다.

    

* #### 작업폴더

  * 작업 폴더 = 워킹트리 + 로컬저장소

  

* #### 원격저장소
  로컬저장소를 업로드하는 곳을 원격저장소라고 부릅니다. 우리가 사용하고 있는 GitHub 저장소가 원격저장소 입니다.

  

* #### Git 저장소

  * 엄밀하게는 로컬저장소를 의미하지만 넓은 의미로 작업 폴더를 의미하기도 한다.

    Git 명령으로 관리할 수 있는 폴더 전체를 일반적으로 Git 프로젝트 혹은 Git 저장소 라고 부릅니다.

    사실 이 말은 상당히 모호합니다만 많은 분이 이렇게 생각하기 때문에 이 책에서도 처음 설명에 Git 저장소라는 단어를 사용했습니다.

    일반적으로 Git 저장소를 작업 폴더와 혼동하기도 하고 워킹트리 + 로컬저장소의 느낌으로 사용하는 듯 합니다만 공식문서에서는 

    로컬저장소와 Git 저장소를 같은 뜻으로 사용하고 있습니다.

    git init 명령을 수행할 때 나오는 메시지도 '비어있는 Git 저장소를 .git에 만듭니다' 라고 나온 것 기억하시죠?




* #### HEAD에 대해...

    1. HEAD는 현재 작업 중인 브랜치를 가리킵니다.        

    2. 브랜치는 커밋을 가리키므로 HEAD도 커밋을 가리킵니다.

    3. 결국 HEAD는 현재 작업 중인 브랜치의 최근 커밋을 가리킵니다.

       

* #### amend 마지막커밋정정 (amend last commit)    

  * 커밋한걸 수정한다.    
    (푸시 완료된 걸 수정하려면 강제 푸시를 해야하며 리스크가 따른다. 푸시 완료된건 혼사 사용하는 브랜치에서만 해야 한다)
  * 추가하고 싶은 변경사항을 스테이지 올리고 "커밋옵션" 드롭다운 버튼을 누르고 "마지막 커밋 정정"을 누른다.
  * 지금 스테이지에 올린 변경사항이 기존 커밋에 추가되면서 기존 커밋이 덮어 쒸워 진다.

|      | 3-way 병합             | rebase                                             |
| :--: | :--------------------- | :------------------------------------------------- |
| 특징 | 머지 커밋 생성         | 현재 커밋들을 수정하면서 대상 브랜치 위로 재배치함 |
| 장점 | 한 번만 충돌 발생      | 깔끔한 히스토리                                    |
| 단점 | 트리가 약간 지저분해짐 | 여러 번 충돌이 발생할 수 있음                      |


* #### 풀 리퀘스트(pull request)

  * 협력자에게 브랜치 병합을 요청하는 메시지를 보내는 것.       

    

* #### 포크(fork)

  * 원본 저장소를 복사해서 원격저장소를 만든다.

  * 남의 원본저장소를 내 계정의 원격저장소로 복사해오는 명령어

  * 평행세계를 만드는 브랜치(branch), 평행우주를 만드는 포크(fork) ?????????? 

    

* #### 리베이스(rebase 재배치)   이해가 잘 안감..

  * 베이스를 다시 잡다.

  * 묵은 커밋을 방금한 커밋처럼     

  * 혼사 사용하는 브랜치에서만 해야 한다.

  * 히스토리를 강제로 조작하기 때문에 다른 사람이 만약 이 히스토리를 보고 있다면 완전히 꼬이고 만다.

  * 강제푸시

  * 충돌 난거 수정 후에는 소스트리 상단에 액션 -> 재배치 계속 를 클랙해서 리베이스를 계속 진행.       
    커밋을 하나씩 비교하면서 충돌이 있나 없나 확인하기 때문에 계속 같은 곳을 수정했다면 [재배치 계속]을 누를 때마다 충돌이 여러 번 날 수 있다.        

    

* #### 체리픽 cherry-pick (다른 브랜치의 커밋 하나만 내 브랜치에 반영하기)

  * 특정 커밋의 변경사항만 현재 브랜치에 가져온다.

    

* #### 초기화 reset (소스트리에서는 "이 커밋까지 현재 브랜치를 초기화")  

  * 모든 기억을 남기면서 브랜치를 되돌리기

  * Soft

    * 되돌린 커밋 시점 이후 추가했던 모든 변경사항을 작업 공간으로 뽑아준다.
    * 커밋 기록은 되돌리지만 그 이후 수정된 파일은 스테이지 위 공간으로 살아나며 당장 커밋 할 수 있다.  
      (mixed 와 차이는 스테이지 위냐 아래냐 당장 커밋하냐 수정하고 커밋하냐 차이정도...)

  * Mixed

    * 되돌린 커밋 시점 이후 추가했던 모든 변경사항을 작업 공간으로 뽑아준다.
    * 커밋 기록은 되돌리지만 그 이후 수정된 파일은 스테이지 아래 공간으로 살아나며 마음대로 다시 수정 할 수 있다..        

  * Hard

    * 모든 기억을 지우며 브랜치를 되돌리기
    * 되돌린 커밋 시점 이후 추가했던 모든 변경사항은 삭제 된다.

  * 히스토리를 강제로 조작하기 때문에 다른 사람이 만약 이 히스토리를 보고 있다면 완전히 꼬이고 만다.        

  * 강제푸시

    

* #### 되돌리기 revert (소스트리에서는 커밋 되돌리기)

  * 커밋의 변경사항을 되돌리는 새로운 커밋 만들기

  * 설명에 'Revert "기존에 작성된 설명"' 처럼 커밋이 생성됨

  * 되돌아 가는 커밋전 시점으로 돌아간다는걸 명심.
    (ex: "파일추가" 커밋 으로 되돌리면 파일추가 전 상태로 돌아감 파일추가 후 상태가 아니라 ...실수 조심)

  * reset 명령어로 커밋을 마치 없었던 일처럼 되돌리는 방법을 배웠습니다. 하지만 모두가 함께 쓰는 브랜치라 이력관리가      
    중요하다면 이렇게 쥐도 새도 모르게 없었던 일처럼 만드는 것보다 변경사항을 되돌리는 새로운 커밋을 만드는 것이 더 좋습니다.

    

* ### 스태시 stash 

  * 작업공간에 변경사항을 잠시 다른 곳에 저장 

  * Pull 이나 브랜치 이동 작업에 수월

  * tracked상태 (추적중 - 한번이라도 Git에 올렸던 상태)인 파일들만 들어갑니다. 신규파일(untracked:추적안됨) 은 해당 안됨

  * 스태시를 계속 사용 할 것이 아니면 사용후 삭제..

  * 스태시를 적용하면 변경사항이 다시 작업 공간으로 튀어 나온다.

    

git status Git 워킹트리의 상태를 보는 명령으로, 매우 자주 사용합니다. 워킹트리가 아닌 폴더에서 실행하면 오류가 발생합니다.
git status -s git status 명령보다 짧게 요약해서 상태를 보여주는 명령으로, 변경된 파일이 많을 때 유용합니다.




| 명령어 | 설명 | 비고 |
|:----------|:----------|:----------|
|pwd|현재폴더의 위치를 확인 합니다.|
|la -a|현재 폴더의 파일 목록을 확인합니다.|
|cd|홈 폴더로 이동합니다.<br>홈 폴더는 사용자 이름과 폴더명이 같고 내 문서 폴더의 상위 폴더 입니다.|
|cd <폴더이름>|특정 위치의 디렉토리로 이동합니다.|
|cd ../ |현재 폴더의 상위 폴더로 이동합니다. |
|mkdir <새폴더이름> |현재 폴더의 아래에 새로운 폴더를 만듭니다. |
|echo "Hello Git" |메아리라는 뜻 <br>화면에 " " 안의 문장인 "Hello Git"을 표시합니다.|
</br>

## #git config (옵션)
### 우선순위 :  지역 옵션 > 전역옵션 > 시스템 옵션     
+ 시스템 옵션 PC전체의 사용자가 유효한 옵션
+ 전역 옵션 현재 사용자가 유효한 옵션
+ 지역 옵션 현재 Git 저장소에서만 유효한 옵션    
```sh
git config --global <옵션명>
 #지정한 전역 옵션의 내용을 살펴 봅니다.

git config --global <옵션명> <새로운 값>
 #지정한 전역 옵션의 값을 새로 설정합니다.

git config --global --unset <옵션명>
 #지정한 전역 옵션을 삭제 합니다.

git config --local <옵션명>
 #지정한 지역 옵션의 내용을 살펴봅니다.

git config --local <옵션명> <새로운 값>
 #지정한 지역 옵션의 값을 새로 설정합니다.

git config --local --unset <옵션명>
 #지정한 지역 옵션의 값을 삭제 합니다.    

git config --system <옵션명>
 #지정한 시스템 옵션의 내용을 살펴봅니다.

git config --system <옵션명> <값>
 #지정한 시스템 옵션의 값을 새로 설정합니다.

git config --system --unset <옵션명> <값>
 #지정한 시스템 옵션의 값을 삭제 합니다.      

git config --list
 #현재 프로젝트의 모든 옵션을 살펴봅니다.

git config --global user.name
 #현재 user.name 확인

git config --global user.name "Hong Gil Dong"
 #현재 user.name 등록 및 변경

git config --global user.email
 #현재 user.email 확인

git config --global user.email "HongGilDong@naver.com"
 #현재 user.email 등록 및 변경

git config --global core.editor
=> ex) git config --global core.editor "code --wait" #VS Code로 편집기 변경
=> ex) git config --global -e #확인
```

## #git local 저장소 생성 
```sh
git init
 #현재 폴더에 Git 저장소를 생성합니다. 현재 폴더에는 [.git] 이라는 숨김 폴더가 생성되는데 사실 이 폴더가 로컬저장소 입니다.
 #clone 으로 원격지에서 다운받지 않고 local에서 바로 git 생성할때 사용
```

## #git add       
```sh 
git add 파일1 파일2 ...    
=> ex) git add file1.txt, file2.txt, file3.txt
 # 파일들을 스테이지에 추가합니다.
 # 새로 생성한 파일을 스테이지에 추가하고 싶다면 반드시 add 명령을 사용합니다.
 
 
 git add -p
 git add -p를 사용하면 파일들의 변경점을 hunk 단위로 보여주고, 해당 hunk에 대해 Stage, Skip 등의 action을 취할 수 있습니다. (hunk는 Stage될 수 있는 파일 조각 단위입니다.)
 y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk or any of the remaining ones
a - stage this hunk and all later hunks in the file
d - do not stage this hunk or any of the later hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help

자주 사용되는 명령어는 y, n, q, s, e입니다.

y : 이 hunk를 stage 시킵니다.
n : 이 hunk를 stage하지 않습니다.
q : add 과정을 종료합니다.
s : 이 hunk를 더 작은 단위의 hunk로 나눕니다. 한 hunk에 대해서 1번만 실행할 수 있습니다.
e : 현재 hunk 내용을 직접 편집합니다.
 
```

## #git commit
```sh
git commit
 # 스테이지에 있는 파일들을 커밋합니다.

git commit -a 
 # add 명령을 생략하고 바로 커밋하고 싶을 때 사용합니다.     
 # 변경된 파일과 삭제된 파일은 자동으로 스테이징되고 커밋됩니다.    
 # 주의할 점은 untracked 파일은 커밋되지 않는다는 것 입니다.     

git commit -m "커밋 테스트"
 #  -m (-m은 message의 약자) 메시지 옵션 comment 를 저장할 수 있다.
```

## #git push
```sh
git push origin master
 # 현재 브랜치에서 새로 생성한 커밋들을 원격저장소에 업로드합니다.     

git push [-u] [원격저장소별명] [브랜치이름]
=> ex) git push -u origin master
 # 최초에 -u 옵션으로 업스트림과 브랜치를 지정하면 다음부터는 "git push" 명령어 만으로도 push 가능     
 # -u 옵션으로 브랜치의 업스트림을 등록할 수 있습니다.    
 # 한 번 등록한 후에는 git push만 입력해도 됩니다.    
```

## #git pull 원격저장소(레파지토리) 에서 내려받기
```sh
git pull
=> ex) git pull origin master
 # 원격저장소의 변경사항을 워킹트리에 반영합니다.    
 # 사실은 git fetch + git merge 명령 입니다. 
 # git pull ( pull = fetch + merge ) 
```

## #git fetch
```sh
git fetch [원격저장소별명] [브랜치이름]
 # 원격저장소의 브랜치와 커밋들을 로컬저장소와 동기화 합니다.    
 # 옵션을 생략하면 모든 원격저장소에서 모든 브랜치를 가져옵니다.   
```

## #git merge
```sh
git merge 브랜치이름
 # 지정한 브랜치의 커밋들을 현재 브랜치 및 워킹트리에 반영합니다.    
  
git merge master #현재 브랜치에 master 브랜치 병합 시도     
git merge feature1 #현재 브랜치에 feature1 브랜치 병합 시도     
```
## #git reset 초기화 (소스트리에서는 "이 커밋까지 현재 브랜치를 초기화")
```sh
git reset [파일명]     
 => ex) git reset file1.txt
 # 스테이지 영역에 있는 파일들을 스테이지에서 내립니다.(언스테이징).    
 # 워킹트리의 내용은 변경되지 않습니다.     
 # 옵션을 생략할 경우 스테이지의 모든 변경사항을 초기화합니다.     
 # 세가지 옵션(soft, mixed, hard) default mixed   

git reset --hard HEAD~  # 현재 브랜치를 한 단계 되돌린다.

git reset --hard <이동할 커밋 체크섬> or git reset HEAD~2           
 # 현재 브랜치를 지정한 커밋으로 옮긴다. 작업 폴더의 내용도 함께 변경된다.     

git reset --hard 명령은 아래의 세 명령을 한번에 수행하는 명령이다.    
 # git checkout HEAD~2
 # git branch -f master
 # git checkout master    

HEAD~<숫자>
HEAD~은 헤드의 부모 커밋, HEAD~2는 헤드의 할아버지 커밋을 말한다. 
HEAD~n은 n번째 위쪽 조상이라는 뜻 이다.   

HEAD^<숫자>
HEAD^은 똑같이 부모 커밋이다. 반면 HEAD^2는 두 번째 부모를 가르킨다.        
병합 커밋처럼 부모가 둘 이상인 커밋에서만 의미가 있다.         

- git add 취소 (스테이지에 올린 파일 내리기)
git reset #전체 파일 add 취소
git reset HEAD 파일 #특정 파일 add 취소 

- git commit 취소
git reset HEAD^  # 가장 최신 커밋 1개 취소(삭제)
git reset HEAD^^ # 가장 최신 커밋 2개 취소(삭제)
```

## #git log
```sh
git log 
 # 현재 브랜치의 커밋 이력을 보는 명령입니다.

git log -n<숫자>
 # 전체 커밋 중에서 최신 n개의 커밋만 살펴봅니다.     

git log --oneline --graph --all --decorate    
 # 모든 브랜치들을 보고  싶을 때 사용      
    --oneline : 커밋 메시지를 한줄로 요약    
    --graph : 커밋 옆에 브랜치의 흐름을 GUI와 유사하게 그래프로 보여줍니다.     
    --all : all 옵션이 없을 경우 HEAD와 관계없는 옵션은 보여주지 않습니다.    
    --decorate : (--decorate=short) 브랜치와 태그 등의 참조를 간결히 표시합니다.     

git log --oneline       
 # 간단히 커밋 해시와 제목만 보고 싶을때       

git log --oneline --graph --decorate        
 # HEAD와 관련된 커밋들을 조금 더 자세히 보고 싶을 때      

git log --oneline -n5       
=> ex) git log --oneline -n1
 # 내 브랜치의 최신 커밋을 5개만 보고 싶을 때 사용합니다.   
```

## #git help
```sh
git 도움말 사용 git help <명령어>       
git help status     
git help commit     
git help add        
```

## #git remote
```sh
git remote add <원격저장소 이름> <원격저장소 주소>  
ex) git remote add origin https://github.com/realllbro/javaStudy.git    
 # 원격저장소를 등록합니다.        
 # 원격저장소는 여러 개 등록할 수 있지만 같은 별명의 원격저장소는 하나만 가질 수 있습니다.     
 # 통상 첫 번째 원격저장소를 origin으로 지정합니다.       
 
git remote [-v | --verbose]
git remote add [-t <branch>] [-m <master>] [-f] [--[no-]tags] [--mirror=(fetch|push)] <name> <url>
git remote rename <old> <new>

git remote remove <name>
ex) git remote remove origin

git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
git remote set-branches [--add] <name> <branch>…​
git remote get-url [--push] [--all] <name>
git remote set-url [--push] <name> <newurl> [<oldurl>]
git remote set-url --add [--push] <name> <newurl>
git remote set-url --delete [--push] <name> <url>
git remote [-v | --verbose] show [-n] <name>…​
git remote prune [-n | --dry-run] <name>…​
git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)…​] 
 

git remote -v       
 # 원격저장소 목록을 살펴봅니다.
```
## #git clone
```sh
git clone <저장소주소> [새로운 폴더명]      
=> ex) git clone https://github.com/realllbro/hello-git-cli.git .
 # 끝에 " ." 한칸 띄고 '.'을 찍어야 해당폴더에 생성됨   생략하면 프로젝트 명으로 
 # 하위 폴더가 생성되고 그안에 git 내려받음

=> ex) git clone https://github.com/realllbro/hello-git-cli.git hello-git-cli2
 # 저장소 주소에서 프로젝트를 복제해 옵니다. 이때 새로 생길 폴더명은 생략 가능하며
 # 폴더명을 생략하면 프로젝트 이름과 같은 이름의 폴더가 새로 생성됩니다. 
 # 저장소 주소는 꼭 원격일 필요가 없으며 로컬저장소도 git clone 명령으로 복제할 수 있습니다.  
```

## #git branch 브랜치 생성하기
```sh       
git branch
 # 현재 브랜치 확인        

git branch [-v]
 # 로컬 저장소의 브랜치 목록을 보는 명령으로 -v 옵션을 사용하면 마지막 커밋도 함께 표시됩니다.     
 # 표시된 브랜치 중에서 이름 왼쪽에 *가 붙어 있으면 HEAD 브랜치 입니다.        

git branch [-f] <브랜치이름> [커밋체크섬]       
=> ex) git branch mybranch1
 # 새로운 브랜치를 생성합니다. 커밋체크섬 값을 주지 않으면 HEAD로 부터 브랜치를 생성합니다.        
 # 이미 있는 브랜치를 다른 커밋으로 옮기고 싶을 때는 -f 옵션을 줘야 합니다.        

git branch -r [-v]        
 # 원격 저장소에 있는 브랜치를 보고 싶을 때 사용합니다. 마찬가지로 -v 옵션을 추가하여 커밋 요약도 볼 수 있습니다.

git branch -d <브랜치이름>      
 # 특정 브랜치를 삭제할 때 사용합니다. HEAD 브랜치나 병합이 되지 않은 브랜치는 삭제할 수 없습니다.

git branch -D <브랜치이름>
 # 브랜치를 강제로 삭제하는 명령입니다. -d 로 삭제할 수 없는 브랜치를 지우고 싶을 때 사용합니다.     
```


## #git checkout 
```sh 
git checkout <브랜치이름>    
=> ex) git checkout mybranch1        
=> ex) git checkout -b feature1 #브랜치 생성 및 체크아웃
=> ex) git checkout -b hotfix master #master 로 부터 hotfix 브랜치 생성, 체크아웃
 # 특정 브랜치로 체크아웃할 때 사용합니다. 브랜치 이름 대신 커밋 체크섬을 쓸 수 있습니다.      
 # 하지만 브랜치 이름을 쓰는 방법을 강력히 권장합니다.  

git checkout -b <브랜치이름> <커밋 체크섬>      
 # 특정 커밋에서 브랜치를 새로 생성하고 동시에 체크아웃까지 합니다.        
 # 두 명령을 하나로 합친 명령이기 때문에 간결해서 자주 사용합니다.      

git checkout ee44b66
 # 특정 커밋 버전으로 되돌리기 (버전키에서 7자리)

git checkout -
 # 최신커밋으로 돌리기(버전키 또는 '-' 문자)
```
## #git merge 
```sh
git merge <대상 브랜치>
=> ex) git merge mybranch1
 # 현재 브랜치와 대상 브랜치를 병합할 때 사용합니다.       
 # 병합 커밋(merge commit)이 새로 생기는 경우가 많습니다.      
```

## #git rebase (재배치)
```sh
git rebase <대상 브랜치>        
 # 내 브랜치의 커밋들을 대상 브랜치에 재배치 시킵니다. 
 # 히스토리가 깔끔해 져서 자주 사용하지만 조심해야 합니다.

git rebase --continue 
 # 충돌(conflict) 로 인해 중단된 rebase를 재개 리베이스 작업을 계속 진행
```

## #git tag 
```sh
git tag -a -m <간단한 메시지> <태그이름> [브랜치 또는 체크섬]       
 # -a로 주석 있는(annotated) 태그를 생성합니다.        
 # 메시지와 태그 이름은 필수이며 브랜치 이름을 생략하면 HEAD에 태그를 생성합니다.      

git push <원격저장소 별명> <태그이름>       
=> ex) git push origin v0.1
 # 원격 저장소에 태그를 업로드 합니다.     
```

## #git 현재상태 확인 
```shell
git status
 # 워킹트리의 상태를 보는 명령어
 # git status로 clean한 상태는 '워킹트리 = 스테이지 = HEAD' 커밋의 내용이 모두 똑같다 라는 뜻.
git status -s
 # 명령보다 짧게 요약해서 상태를 보여주는 명령으로, 변경된 파일이 많을 때 유용합니다

git hash-object <파일명>
 #일반 파일의 체크섬을 확인할 때 사용

git show <체크섬>
 #해당 체크섬을 가진 객체의 내용을 표시

git ls-files --stage 
#스테이지 파일의 내용을 표시
#스테이지 파일은 git add 명령을 통해 생성되는데 .git/index 파일이 스테이지 파일입니다.

git cat-file -t <체크섬>
 #해당 체크섬을 가진 객체의 타입을 알려주는 명령

git cat-file -t <객체타입> <체크섬>
=> ex) git cat-file blob ff5bda
 #객체의 타입을 알고 있을 때 해당 파일의 내용을 표시해 줍니다. (git cat-file -t <체크섬> 명령어로 타입 확인)
```

## #git 폴더삭제
```shell
rm -rf 폴더명

# 원격 저장소와 로컬 저장소에 있는 파일을 삭제한다.
$ git rm [File Name]
# 원격 저장소에 있는 파일을 삭제한다. 로컬 저장소에 있는 파일은 삭제하지 않는다.
$ git rm --cached [File Name]

# .idea/modules.xml 파일 삭제
$ git rm --cached .idea/modules.xml
# .idea 폴더 하위의 모든 파일 삭제 
$ git rm --cached -r .idea/

https://gmlwjd9405.github.io/2018/05/17/git-delete-incorrect-files.html

```

* 
