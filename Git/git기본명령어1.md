# 🔥Git 기본 명령어🔥

---

## `git status`

> 현재 작업중인 파일들의 상태를 확인하는 명령어

### 표시 되는 상태종류

- branch: 어떤 브랜치에서 작업이 되고 있는지
- commit: 커밋 여부
- tracking
  - untracked: 작업을 통해 파일의 변경사항이 생겼지만 아직 `staging area`에 저장되지 않아 git이 트랙킹 할 수 없는 상태
  - tracked: 통해 로컬에서 작업한 내용이 `staging area`에 저장되어 있는 상태로 git이 작업된 내용들을 트랙킹 할 수 있으며 Commit이 될 준비가 된 상태
  - 만약 tracked상태로 변경된 파일에 다른 수정사항이 생길 경우 해당 파일은 git이 트랙킹 하고 있기 때문에 새로운 변경사항은 modified로 표시됨

### 자주 사용되는 옵션

- `-s`: short버전으로 status의 내용을 축약하여 간단하게 표시 해주는 옵션(default는 log으로 내용을 상세 하게 표시)

---

## `git add`

> WorkingDirectory(로컬)에서 작업중인 파일들(untracked 상태)을 staging area(traked 상태)로 옮기는 명령어

### 기본적인 사용법

- `git add [fileName].[ext]`: 특정 untracked파일 하나만 선택하여 staging area로 옮김
- `git add *.[ext]`: [ext]에 해당하는 확장자인 모든 untracked 파일들을 staging area에 저장 ex) git add \*.html
- `git add *`: untracked된 파일들 전부 staging area에 저장
- `git add .`: 기본적으로 `git add *` 같음

### `git add *` vs `git add .`

`git add *`는 `.gitignore`에 등록된 파일을 포함해 모든 파일을 staging area에 저장하지만 `git add .`의 경우 `.gitignore`에 등록된 파일은 staging area에 저장하지 않아 `git add .`를 사용하는것을 추천

---

## `git commit`

> staging area에 저장되어 있는 변경사항들을 Git Directory로 옮기며 실질적인 버전 히스토리를 만드는 명령어

### 특징

커밋 을 할때 커밋 메시지는 필수 이며 특정 옵션 없이 사용 할 경우 설정된 에디터가 켜지며 버전 히스토리에 저장할 커밋 단위에 대한 설명을 작성해야 커밋 할 수 있음.

### 자주 사용되는 옵션

- `-m 'COMMIT MESSAGE'`: 커밋 명령어의 실행과 함께 메시지도 같이 작성하는 옵션
- `-am 'COMMIT MESSAGE'`: Working Directory에서 작업한 단위 전부 작성된 메시지와 함께 staging area에 저장하면서 커밋하는 옵션

- `--amend`: 가장 최근 커밋 수정

---

## 번외 - `.gitignore`

특정 파일들 or 디렉토리 에 대해서 git이 트랙킹 하는것을 원치 않는 경우 .gitignore 파일을 만들고 등록하면 된다.
ex) javascript진영의 라이브러리 의존성들을 모아놓은 node_modules의 경우 상당한 용량을 차지 하므로 원격 서버에 저장되지 않도록 보편적으로 .gitignore에 등록함
