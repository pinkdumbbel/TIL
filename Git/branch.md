# 🔥Branch🔥

---

## `git branch`

> git을 통해 협업을 한다면 필수 적으로 사용하는 기능 브랜치 명과 옵션없이 커맨드 입력시 현재 로컬 리파지토리에 있는 branch 리스트를 보여줌

### 자주 사용되는 옵션

- `[브랜치명]` : 해당 브랜치명으로 브랜치 생성
- `--all`: 현재 로컬 리파지토리 에 있는 브랜치 뿐만아니라 원격 리파지토리에 있는 브랜치 목록도 보여줌

- `-v`: 현재 로컬 리파지토리에 있는 브랜치 목록을 최신 커밋 버전과 함께 보여줌

- `--merged`: 메인 브랜치에 머지된 브랜치 목록만 보여줌 만약 브랜치 생성후 커밋이 없다면 그 브랜치들 까지 포함하여 보여줌

- `--no-merged`: 브랜치 생성후 특정 커밋이 있고 메인 브랜치에 머지 되지 않은 브랜치 목록을 보여줌

- `-d [브랜치명]`: 브랜치 삭제

- `--move [브랜치명] [변경할 브랜치명]`: 브랜치명 변경

---

## `git checkout [브랜치명 or 커밋해쉬]`

> 브랜치 변경을 할 수 있게 해주는 명령어로 특정 커밋버전으로 이동 가능 함

### 자주 사용되는 옵션

- `-b [브랜치명]`: 브랜치를 만들면서 동시에 해당 브랜치로 변경

---

## `git cherry-pick [커밋해쉬]`

> 특정 브랜치에서 작업된 커밋 히스토리 중 특정 커밋만 merge 하는 명령어