## `git restore`

> working directory 혹은 staging area 에 있는 작업 내용을 초기화 할때 사용 **git add** 와 마찬가지로 특정 파일 또는 전체 파일을 선택적으로 초기화 할 수 있음

### 자주 사용하는 옵션

- `--staged`: **staging area**에 올라가 있는 파일들을 working directory로 옮김

- `--source=[특정커밋]`: 특정 커밋으로 부터 파일을 초기화 커밋해쉬 및 HEAD포인터 로 특정 커밋을 가리킬수 있음 초기화 되면 특정 커밋 이후의 히스토리는 삭제됨

---

## `git reset [커밋해쉬 or HEAD포인터]`

> 특정커밋으로 히스토리를 초기화 하고 싶을때 사용하는 명령어

### 자주 사용하는 옵션

- `--mixed`: **working directory**에 삭제된 커밋 내용이 옮겨지며 생략 가능한 옵션

- `--soft`: **staging area**에 삭제된 커밋 내용이 옮겨지며 생략 가능한 옵션

- `--hard`: 삭제된 커밋 내용이 **working directory** 와 **staging area**에 남지 않고 전부 삭제됨

### ※주의 사항

reset 명령어로 커밋 히스토리 삭제후 다시 원복 하고 싶다면 `git reflog`명령어로 해쉬커밋을 찾고 다시 `git reset --hard [커밋해쉬]`를 통해 다시 원복 시킬수 있다.
하지만 커밋이 된 내용들만 원복 되기 때문에 초기화 시점에 working directory 혹은 staging area에 있던 변경 사항들은 원복 되지 않는다

---

## `git revert [커밋해쉬 or HEAD포인터]`

> 특정 커밋의 변경사항을 삭제, 취소 해주는 명령어로 서버에 이미 업로드 된 커밋이라면 reset 혹은 resotre를 사용하기 보다 revert를 사용하는게 좋음

### reset 과 차이점

**revert**는 **reset**과 다르게 커밋을 삭제하지 않고 revert 커밋을 추가로 생성함

### 자주 사용하는 옵션

- `--no-commit`: revert결과를 커밋 하지 않고 staged상태로 유지 할때 사용하는 옵션

---

## `git reflog`

> HEAD가 가리키고 있던 내용들을 전부다 보여주는 명령어
