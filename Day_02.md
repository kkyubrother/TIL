# GIT
## Switch, Restore
* 기존의 `checkout` 명령어가 `switch/restore` 명령어로 나뉘어짐
* `checkout`: Switch branches or restore working tree files
    * 분기 전환 또는 작업 트리 파일 복원 
    * 가진 기능이 많다.
* `switch`: Switch branches
    * 분기 전환
* `restore`: Restore working tree files
    * 작업 트리 파일 복원

### Switch
```Bash
# 단순 브랜치 전환
$ git switch target_branch_name

# 브랜치 생성 밎 전환
$ git switch -c target_branch_name

# 특정 지점에서 브랜치 생성 및 전환
$ git switch -c target_branch_name 1234abcd
```
### Restore
```Bash
# 파일 수정 복원
$ git restore README.md

# 스테이지 > 작업 영역
$ git restore --staged README.md
```

[참고자료](https://blog.outsider.ne.kr/1505)

## Forking Workflow
1. 저장소를 fork 한다.
2. [local] `git remote add upstream [원본 URL]`
3. [local] `git switch -c feature/new`
4. [local] 기능 추가를 위해 branch 생성 및 기능 구현
5. 기능 구현 후 원격 저장소에 브렌치 반영
6. [server] 서버에 새로운 브렌치 생성됨
7. 원본(upstream)에 복제(origin)을 pull 하라고 요청함
    * base_repository: 수신받을 레포
    * head_repository: 전달할 레포
    * 


# RUST
[교재: 러스트 프로그래밍 공식 가이드(교보문고)](http://www.kyobobook.co.kr/product/detailViewKor.laf?mallGb=KOR&ejkGb=KOR&barcode=9791188621729)

## 