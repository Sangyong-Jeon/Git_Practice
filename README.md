# Git
운영체제 : MacOS Monterey ver 12.5.1

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

```zsh
git config --global init.defaultBranch main
```
기본 브랜치 이름을 `master` -> `main`으로 변경

<br>

```zsh
git config --global core.editor "code --wait"
```
git 기본 에디터가 Vim -> VSCode로 변경

<br>

```zsh
git config --list
```
Git 환경설정에 대한 내용 확인 (name, email 등등)

<br>

```zsh
git config --global user.name "홍길동"
git config --global user.email "홍길동@naver.com"
```
name과 email을 변경하는데 `--global`을 사용하여 전역으로 설정함

<br>

```zsh
git config --unset user.name
git config --unseet user.email
```
name과 email을 지우는 경우

<br>

```zsh
git config --unset --global user.name
git config --unset --global user.email
```
global로 설정한 경우 반드시 global 옵션을 추가해야 해당 값이 삭제됨.
