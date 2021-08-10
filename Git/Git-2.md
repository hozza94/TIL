## Git-2

### 좋은 git 커밋 메시지를 작성하기 위한 7가지 약속

1. 제목과 본문을 한 줄 띄워 분리하기
2. 제목은 영문 기준 50자 이내로
3. 제목 첫글자를 대문자로
4. 제목 끝에 `.` 금지
5. 제목은 `명령조`로
6. 본문은 영문 기준 72자 마다 줄 바꾸기
7. 본문은 `어떻게`보다 `무엇을`,`왜`에 맞춰서 작성하기

> [commit message](https://meetup.toast.com/posts/106)

### commit message를 위한 영어사전

1. Fix
2. Add
3. Remove
4. Use
5. Refactor
6. Simplify
7. Update
8. Improve
9. Make
10. Implement
11. Revise
12. Correct
13. Ensure
14. Prevent
15. Avoid
16. Move
17. Allow
18. Verify
19. Set
20. Pass

> [commit dict](https://blog.ull.im/engineering/2019/03/10/logs-on-git.html)

### .gitignore

- *.txt

- data/

  > [gitignore.io](https://gitignore.io/)

### github Pages

- make username.github.io repo
- [hozza.io](hozza94.github.io)

### Push & Pull

- web 상에서 add README.md 해서 추가 하고 local에서 새 파일을 만들고 푸시하는경우 발생하는 에러

```bash
$ git push origin main
To https://github.com/hozza94/test.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/hozza94/test.git'
# 원격 저장소 작업 != 로컬 저장소 작업 (커밋)
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. 
# 먼저 원격 저장소 변경사항들을 통합하는 것을 원할 것.. (다시 push 하기 전에)
You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

- 원격저장소에 있는 commit을 먼저 pull 한다.

```bash
$ git pull origin main
```

- merge commit 발생 -> 로컬과 원격저장소의 commit을 합쳐서 push

```bash
Merge branch 'main' of https://github.com/hozza94/test
# Please enter a commit message to explain why this merge is necessary,
# especially if it merges an updated upstream into a topic branch.
#
# Lines starting with '#' will be ignored, and an empty message aborts
# the commit.
```

### Branch

- 독립된 작업 흐름을 만들어 나가기 위해 사용

#### command

```bash
$ git branch newbranch # 생성
$ git checkout newbranch # 이동
$ git checkout -b newbranch # 생성 + 이동
$ git branch # 조회
(master/main) $ git merge branchname
$ git branch -d branchname
```

- 새로운 브랜치에서 작업

```bash
$ git log --oneline
978e456 (HEAD -> new_branch) 추석
5a2e292 (origin/main, main) add b.mp3
07f3bc4 Merge branch 'main' of https://github.com/hozza94/test
2e6836f update
c3c3e17 Create README.md
cd8a45f first commit
```

- 새로운 브랜치와의 merge

```bash
$ git merge new_branch
Merge made by the 'recursive' strategy.
 end.txt                        | 0
 "\354\266\224\354\204\235.txt" | 0
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 end.txt
 create mode 100644 "\354\266\224\354\204\235.txt"
```

> 버전관리시 main(master) 브랜치는 항상 동작하는 배포 가능한 코드로 등록

### Pull & Request

```bash
$ git push origin otherbranchname
```

- 이 후에는 github에 들어가서 pull request를 요청하고 대표자의 판단을 기다린다.

### Fork

- 다른 사람의 저장소를 복사해 가져오는 것
- 내 저장소로 만든 후 clone commit push 작업
- pr(pull request)를 본 사람의 저장소로 보냄

### Fetch

- 변경사항을 가지고 옴. -> 내가 직접 반영하려면 merge

### Restore

- `git add` 명령을 취소하고 싶을 때
- 이전 `commit`상태로 되돌릴 때

```bash
$ git restore --staged <file>..."" to unstaging
```

### amend

- 커밋 메시지를 변경할때 사용

``` bash
$ git commit --amend
```

> :red_circle: ​주의 : commit 이 바뀜

### Reset

- 커밋을 지우는 명령어 (그냥 삭제)
- push하기 전에는 마음껏 reset

```bash
$ git reset --hard commitkey # 모든 단계를 지움
$ git reset --mixed commitkey # 커밋은 지우지만 작업물은 남김
$ git reset --soft commitkey # 커밋은 지우지만 좀더 많은것을 남김?
```

### Revert

- 커밋을 지우는 명령어 (버전을 되돌렸다 라는 커밋을 발생 시키면서)
- push된 이후에는 revert를 해서 기록을 남기는것이 중요함

```bash
$ git revert commitkey
```

### Stash

- 작업중에  pull을 해야하는 경우 임시공간에 현재 작업중인것을 저장한다

```bash
$ git stash # 보관
$ git stash pop # 저장된 임시작업을 받아옴
```

### Reference

>[GIT_BOOK](https://git-scm.com/book/ko/v2)

