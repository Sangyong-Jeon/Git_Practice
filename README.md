# Git

### 구조

[ 작업폴더 ] --`git add`--> [ Staging Area ] --`git commit`--> [ Repository ]

- Staging Area : 커밋할 파일들을 골라놓는 곳
  - 이 영역에 파일을 넣는 행위를 staging(스테이징)이라 함
  - `git add` 명령어로 스테이징 함
- Repository : 커밋된 파일의 버전들을 모아놓는 곳
  - 작업폴더 안에 숨겨져 있는 `.git`폴더를 열면 볼 수 있음

<br>

---

### 설치방법

우선 homebrew를 설치했다는 가정하에 진행함

```zsh
brew install git
```
위 코드를 입력해서 깃 설치<br>
만약 homebrew가 싫다면 https://sourceforge.net/projects/git-osx-installer/ 에서 다운받아 우클릭 -> 열기 눌려서 설치


---

### 기본 명령어

- 저장소 생성
  - 새로운 Git 저장소(repository)를 생성할 때 사용하는 명령어
  - 현재 디렉토리를 기준으로 Git 저장소 생성 (`.git` 디렉토리 생성)
  - `Initialized empty Git repository in /Users/yong/Document/.../.git/`
  - `.git`에는 Git이 버전관리를 하기 위한 메타 정보가 담겨져 있으므로 지우면 Git 저장소 변경 이력 소실되고 일반 디렉토리로 변경됨.
  
  <br>
  
  ```zsh
  git init
  ```

<br>

- 기본 브랜치 이름 변경
  - `master` -> `main` 변경
  
  <br>
  
  ```zsh
  git config --global init.defaultBranch main
  ```

<br>

- Git 기본 에디터 변경
  - Vim -> VSCode 변경
  
  <br>
  
  ```zsh
  git config --global core.editor "code --wait"
  ```

<br>

- Git 환경 설정 확인
  - name, email 등등
  
  <br>
  
  ```zsh
  git config --list
  ```

<br>

- Git 환경 설정
  - name과 email 변경할 때 `--global`을 사용하여 전역으로 설정
  
  <br>
  
  ```zsh
  git config --global user.name "홍길동"
  git config --global user.email "홍길동@naver.com"
  ```

<br>

- Git 환경 설정 삭제
  - name과 email 지우는 경우
  
  <br>
  
  ```zsh
  git config --unset user.name
  git config --unseet user.email
  ```
  - 전역(global)로 설정한 경우 반드시 `--global` 옵션을 추가해야 해당 값이 삭제됨
  
  <br>

  ```zsh
  git config --unset --global user.name
  git config --unset --global user.email
  ```

<br>

- 특정 파일 스테이징(staging)
  - commit 할 파일들을 정해서 staging area에 넣음
  
  <br>
  
  ```zsh
  git add 파일명
  ```
  - 여러 파일 스테이징
  
  <br>
  
  ```zsh
  git add 파일명1 파일명2
  ```
  - 작업폴더의 모든 파일을 전부 스테이징
  
  <br>
  
  ```zsh
  git add .
  ```
  
<br>

- 커밋(commit)
  - staging area에 있는 파일들을 버전별로 repository(저장소)에 저장함
  - commit할 때 -m 뒤에 메시지 입력 가능함
  
  <br>
  
  ```zsh
  git commit -m '메모하는곳'
  ```

<br>

- 변경 사항 체크
  - 변경된 파일, 스테이징된 파일 등 알려줌
  
  <br>
  
  ```zsh
  git status
  ```
  
<br>

### Commit(커밋) 관련 명령어

- 커밋 기록 확인
  - `--graph` 옵션 넣으면 그래프로 그려줌
  - commit 기록을 한 눈에 파악할 때 사용
  - `oneline` 넣으면 한줄씩 간단요약
  <br>
  
  ```zsh
  git log
  git log -3
  git log --pretty=oneline
  git log --all --oneline
  git log --all --oneline --graph
  ```
  
<br>

- 바로 전 commit과 현재 코드의 차이점 비교
  - `git diff`는 엔터키나 스페이스바 변동사항도 다 알려줘서 그대로 사용을 잘 안함
  - 깃 로그를 통해 과거의 특정 커밋과 현재 파일을 비교할 때는 커밋id를 명시해줌
  - 특정 커밋id를 2개적으면 두개를 비교함
  
  <br>
  
  ```zsh
  git diff
  git diff 커밋id
  git diff 커밋id1 커밋id2
  ```

<br>

- 바로 전 commit과 현재 코드의 차이점 비교2
  - `git diff`보다 시인성 좋게 만들어줌
  - 기본 사용법은 `git diff`와 동일
  - 하지만 요새 이런 비교 명령어보단 IDE에 있는 부가기능이 더 잘되어있음(ex.VSCode의 Git Graph 등)
  
  <br>
  
  ```zsh
  git difftool
  git difftool 커밋id
  git difftool 커밋id1 커밋id2
  ```

<br>

### branch(브랜치) 관련 명령어

- 브랜치 생성
  - 프로젝트 사본을 만드는 것
  
  <br>
  
  ```zsh
  git branch 브랜치이름
  ```

<br>

- 브랜치 이동
  - 예전엔 `git checkout 브랜치명`을 입력했음
  - 현재 브랜치가 어딘지 알고싶으면 `git status` 입력
  - 브랜치 리스트를 알고싶으면 `git branch` 입력
  
  <br>
  
  ```zsh
  git switch 브랜치이름
  git checkout 브랜치이름
  ```

<br>

- 브랜치 합치기
  - main 브랜치에 새로만든 브랜치를 합치고 싶으면 main 이동 후 merge 입력
  - 각 브랜치에서 동일 파일을 수정해서 충돌 일어나면 HEAD가 현재 브랜치 파일내용이고, 수정 후 해당 파일 스테이징하여 커밋하면 완료
  
  <br>
  
  ```zsh
  git switch main
  git merge 새로만든 브랜치명
  ```
