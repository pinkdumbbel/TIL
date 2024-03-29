# 🔥Rebase🔥

## `git rebase`

> merge와 함께 git 시스템 에서 브랜치를 병합하는 방법 three-way 머지의 상황에서 포인터를 메인 브랜치의 최신 커밋으로 옮겨 fast-forward 머지를 하여 머지커밋 로그를 안남기고 깔끔하게 히스토리를 관리 할 수 있다.

---

### 자주 사용되는 옵션

- `--onto [기준 브랜치] [특정 브랜치] [특정 브랜치로 부터 파생된 브랜치]`: main브랜치 외의 다른 브랜치에서 파생된 브랜치의 포인터를 기준 브랜치로 변경할때 사용하는 옵션

- `-i [커밋해쉬]`: 최신커밋 외의 이전 커밋에 대한 내용을 변경 할때 사용하는 명령어

---

### ※주의점

특정 브랜치에서 다른 사람들과 함께 작업을 하고 있고 커밋 히스토리가 이미 push되어 서버에 업로드 되어 있는 상태에서 rebase를 사용하게 되면 **git 시스템 상 포인터가 변경되면 새로운 커밋을 만들기 때문에 겉으로 보기엔 동일한 커밋 같지만 다른 커밋이 생성 되며 rebase를 한 상태에서 서버에 업로드 할 경우 기존에 있던 히스토리들과 충돌이 발생함** 따라서 브랜치에서 혼자 작업 하거나 로컬 환경에서만 작업을 하는 경우에 사용하는것이 바람직함

---

### 사용 방법

1. three-way merge 상태에서 `git rebase main`명령어를 통해 기준이 되는 포인터를 main브랜치의 최신 커밋으로 변경

2. main 브랜치로 이동후 `git merge [브랜치명]`명령어를 통해 특정 브랜치의 히스토리를 fast-forward머지 함

3. merge된 브랜치들은 삭제

4. 로그 확인
