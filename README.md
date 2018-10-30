# 2017261024_기수연_안드로이드 프로그래밍
## git 명령

### 기본 개념
  + **Push 푸시** 
         <pre><code> 로컬 저장소(데스크탑)에서 커밋한 소스를 원격 저장소에 전송. 서버에 새로운 버전을 업로드 하는 것</pre></code> 
  + **Pull 풀** 
         <pre><code>서버(원격 저장소)에 저장된 프로젝트를 로컬(데스크탑)으로 내려받는 것</pre></code>
  + **Commit 커밋**
          <pre><code>프로젝트의 소스코드가 변경되면 이것을 저장소에 저장 즉, 버전을 생성하는 것</pre></code>
  + **Merge 병합**
         <pre><code>버전 관리 중인 프로젝트 라인과 다른 프로젝트의 라인을 합치는 것</pre></code>
  + **Fetch 패치**
          <pre><code>원격 저장소에 등록된 내용을 로컬에 다운받지 않고 서버에서 확인하는 작업으로 
          수정된 내용이 덮어쓰기 되는 것을 방지하기 위해서 사용</pre></code>
  + **Branch 브랜치** 
           <pre><code>프로젝트 진행 중간에 새로운 기능을 추가하거나
           앞 내용은 같은데 뒷 내용이 다른 독립적인 개발 라인을 만들 때 사용하는 것 </pre></code>
* * *           
### 구조
코드는 아래 세 단계에 걸쳐 저장된다.

<pre><code> 스테이징 -> 커밋 -> 원격저장소

git add {파일명} 으로 파일을 스테이징 상태에 넣는다.
git commit 으로 스테이징 상태에 있는 모든 변경사항을 커밋한다. 여기까지가 로컬에서의 작업
git push 로 커밋된 저장소를 원격 저장소로 밀어넣는다.</pre></code>

### 기본 명령어
저장소 생성

<pre><code>git init</pre></code>

원격 저장소로부터 복제

<pre><code>git clone {url}</pre></code>

변경 사항 체크

<pre><code>git status // </pre></code>

특정 파일 스테이징

<pre><code>git add {파일명}</pre></code>

변경된 모든 파일 스테이징

<pre><code>git add * </pre></code>

커밋

<pre><code>git commit -m “{변경 내용}”</pre></code> 

원격으로 보내기

<pre><code>git push origin master </pre></code>

원격저장소 추가

<pre><code>git remote add origin {원격서버주소}</pre></code> 
* * *
### Commit
커밋 합치기

<pre><code>git rebase -i HEAD~4 // 최신 4개의 커밋을 하나로 합치기</pre></code>

커밋 메세지 수성

<pre><code>$ git commit --amend // 마지막 커밋메세지 수정(ref)</pre></code>

간단한 commit방법

<pre><code>$ git add {변경한 파일병}
$ git commit -m “{변경 내용}"</pre></code>

커밋 이력 확인

<pre><code>$ git log // 모든 커밋로그 확인
$ git log -3 // 최근 3개 커밋로그 확인
$ git log --pretty=oneline // 각 커밋을 한 줄로 표시 </pre></code>

커밋 취소

<pre><code>$ git reset HEAD^ // 마지막 커밋 삭제
$ git reset --hard HEAD // 마지막 커밋 상태로 되돌림
$ git reset HEAD * // 스테이징을 언스테이징으로 변경, ref </pre></code>

* * *
### Branch
master 브랜치를 특정 커밋으로 옮기기

<pre><code>git checkout better_branch
git merge --strategy=ours master    # keep the content of this branch, but record a merge
git checkout master
git merge better_branch            # fast-forward master up to the merge </pre></code>

브랜치 목록

<pre><code>$ git branch // 로컬
$ git branch -r // 리모트 
$ git branch -a // 로컬, 리모트 포함된 모든 브랜치 보기 </pre></code>

브랜치 생성

<pre><code>git branch new master // master -> new 브랜치 생성
git push origin new // new 브랜치를 리모트로 보내기 </pre></code>

브랜치 삭제

<pre><code>git branch -D {삭제할 브랜치 명} // local
git push origin :{the_remote_branch} // remote </pre></code>

빈 브랜치 생성

<pre><code>$ git checkout --orphan {새로운 브랜치 명}
$ git commit -a // 커밋해야 새로운 브랜치 생성됨
$ git checkout -b new-branch // 브랜치 생성과 동시에 체크아웃 </pre></code>

리모트 브랜치 가져오기

<pre><code>$ git checkout -t origin/{가져올 브랜치명} // ref </pre></code>

브랜치 이름 변경

<pre><code>$ git branch -m {new name} // ref </pre></code>
* * *
### Tag
태그 생성

<pre><code>git tag -a {tag name} -m {tag message} {commit hash}
git tag {tag name} {tag name} -f -m "{new message}" // Edit tag message </pre></code>

태그 삭제

<pre><code>git tag -d {tag name}
git push origin :tags/{tag name} // remote </pre></code>

태그 푸시

<pre><code>git push origin --tags
git push origin {tag name}
git push --tags </pre></code>



