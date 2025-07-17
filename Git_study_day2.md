# Git_02

 **Remote Repository 연결**

- 로컬 저장소에 원격 저장소 추가
```python
git remote add repo_name remote_repo_url
```
- 등록된 원격 저장소 목록 확인
  
```python
git remote -v
```

- 등록된 원격 저장소 삭제
  
```python
git remote rm repo_name
```
---

 **Push**
  
  - repo_name 이라는 이름의 원격 저장소에 master이라는 이름의 branch를 PUSH   
  -- 최초 push시에는 GitHub로부터 인증서(git credential) 발급 필요
```python
git push repo_name master
```

ex) git add > git commit > git push

- ---

  
**Pull & Clone**

- 원격 저장소 전체를 복제
```python
git clone remote_repo_url
```

- repo_name 이라는 이름의 원격 저장소에서 변경사항만을 master이라는 이름의 branch로 PULL
```python
git pull repo_name master
```

- ---

**gitignore**

- gitignore : Git에서 **특정 파일이나 디렉토리를 추적하지 않도록 설정**하는 데 사용되는 텍스트 파일

  1. .gitignore 파일 생성(파일명 앞에 '.' 입력, 확장자 없음)
  2. a.txt와 b.txt 파일 생성
  3. gitignore 파일을 열고 a.txt라고 작성
  4. git init
  5. git status

- gitignore 주의사항 : 이미 git의 관리를 받은 이력이 있는 파일이나 디렉토리는 나중에 gitignore에 작성해도 적용되지 않음   
따라서, 이 경우 `git rm --cached` 를 통해 git cache에서 삭제 필요
---

- README.md 파일은 보통 repo에 대한 전체적인 설명을 할 때 주로 이용한다!
---

**Revert**
- revert :  단일 commit 실행 취소, log에 기록 남음   
  순방향 실행 취소 작업으로, commit 기록에서 commit을 삭제하거나 분리하는 대신, 지정된 변경 사항을 반전시키는 새 commit 생성   
  기록의 무결성과 협업의 신뢰성을 높임

1. 삭제하고자 하는 commit id를 REVERT
```python
git revert <commit_id>
```
2. vim 편집기 실행 -> 저장 후 종료(by `:wq`)

---

**Reset**
- reset :  시계를 마치 과거로 돌리는 것처럼 특정 commit 시점으로 되돌아감. 되돌아간 commit 이후의 commit은 모두 삭제

```python
git reset [option] <commit_id>
```
[option] : soft / mixed(default) / hard
  1. soft : 삭제된 commit의 기록을 staging area에 남김(수정 불가)
  2. mixed : 삭제된 commit의 기록을 working directory에 남김(수정 가능)
  3. hard : 삭제된 commit의 기록을 남기지 않음
   
참고) git reflog 이용하면 복구 가능


