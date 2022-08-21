# 🔥Stash🔥

## `git stash push(git stash)`

> working directory 에서 작업이 완료 되지 않아 커밋 하기 어려운 상태에서 특정 브랜치로 이동을 해야 되는 경우 혹은 특정 작업을 여러가지 방법으로 해야하는 경우 유용하게 사용 할 수 있음

---

### 자주 사용되는 옵션

- `-m [stash이름]`: 현재 작업내용을 stash 스택에 push 될 때 특정 이름으로 push

- `--keep-index`: staging area 상태를 유지하면서 stash함

- `-u`: untracked 파일들도 stash할 수 있게 해줌

- `list`: stash 스택에 쌓여 있는 목록을 보여줌

- `show [id]`: stash 스택에서 id에 해당하는 stash의 변경사항을 확인 할 수 있음 `-p`옵션을 추가로 사용하면 더 자세히 보여줌

- `apply [id]`: id를 생략하면 스택의 가장 상단의 stash가 staging area로 옮겨지며 id를 입력하면 해당하는 특정 stash가 옮겨지며 stash 목록에는 남아 있음

- `pop`: 스택의 가장 상단의 stash가 staging area로 옮겨지며 해당 stash는 목록에서도 같이 삭제됨

- `drop [id]`: 해당하는 id의 stash를 목록에서 제거

- `clear`: stash목록 전부 삭제

- `branch [브랜치명]`: stash 스택의 내용을 적용하면서 새로운 브랜치를 만들때 사용
