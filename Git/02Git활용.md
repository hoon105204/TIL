# 깃허브 특강 2일차

## 1. clone & pull

### 1.1 git clone

- 원격 저장소의 커밋 내역을 모두 가져와서, 로컬 저장소를 생성하는 명령어
- `git clone <원격 저장소 주소>`의 형태로 작성

```
$ git clone https://github.com/edukyle/TIL.git
Cloning into 'TIL'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```

- git clone을 통해 생성된 로컬 저장소는 `git init`과 `git remote add`가 이미 수행되어 있다.

### 1.2 git pull

- 원격 저장소의 변경 사항을 가져와서, 로컬 저장소를 업데이트 하는 명령어
- `git pull <저장소 이름> <브랜치 이름>`의 형태로 작성

```
$ git pull origin master
From https://github.com/edukyle/git-practice
 * branch            master     -> FETCH_HEAD
Updating 6570ecb..56809a9
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)


[풀이]
git 명령어를 사용할건데, origin이라는 원격 저장소의 master 브랜치의 내용을 가져온다(pull).
```



## 2. .gitignore

> 특정 파일 혹은 폴더에 대해 Git이 버전 관리를 하지 못하도록 지정하는 것

- .gitignore 예시

<img src="https://hphk.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffd7bd601-9433-418a-b08e-7b027db9a301%2FUntitled.png?table=block&id=26ab9b0d-1b59-48e3-9c60-b3f8f15fee87&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1060&userId=&cache=v2" alt="img" style="zoom:80%;" />



## 3. 브랜치(Branch)

### 3.1 브랜치(Branch)란?

<img src="https://blog.kakaocdn.net/dn/t3Ih1/btqFvuOfQFZ/HrlGV5obNZ9NNRmOnEbkok/img.png" alt="img" style="zoom:67%;" />

- `브랜치`란 나뭇가지처럼 여러 갈래로 작업 공간을 나누어 독립적으로 작업할 수 있도록 도와주는 Git의 도구
- **장점**
  1. 브랜치는 독립 공간을 형성하기 때문에 원본(master)에 대해 안전함
  2. 하나의 작업은 하나의 브랜치로 나누어 진행되므로 체계적인 개발이 가능
  3. 특히나 Git은 브랜치를 만드는 속도가 굉장히 빠르고, 용량도 적게 듦

### 3.2  git branch

> 브랜치 조회, 생성, 삭제 등 브랜치와 관련된 Git 명령어

```
# 브랜치 목록 확인
$ git branch

# 원격 저장소의 브랜치 목록 확인
$ git branch -r

# 새로운 브랜치 생성
$ git branch <브랜치 이름>

# 특정 커밋 기준으로 브랜치 생성
$ git branch <브랜치 이름> <커밋 ID>

# 특정 브랜치 삭제
$ git branch -d <브랜치 이름> # 병합된 브랜치만 삭제 가능
$ git branch -D <브랜치 이름> # (주의) 강제 삭제 (병합되지 않은 브랜치도 삭제 가능)
```

### 3.3 git switch

> 현재 브랜치에서 다른 브랜치로 `HEAD`를 이동시키는 명령어 `HEAD`란 현재 브랜치를 가리키는 포인터를 의미합니다.

```
# 다른 브랜치로 이동
$ git switch <다른 브랜치 이름>

# 브랜치를 새로 생성과 동시에 이동
$ git switch -c <브랜치 이름>

# 특정 커밋 기준으로 브랜치 생성과 동시에 이동
$ git switch -c <브랜치 이름> <커밋 ID>
```

- 브랜치 그래프는 `git log --oneline --all --graph`를 통해 보거나 혹은 툴을 다운받아 볼 수 있다.

<img src=".\image\image-20220414173311338.png" alt="image-20220414173311338" style="zoom: 80%;" />

## 4. git merge

- 분기된 브랜치들을 하나로 합치는 명령어
- `git merge <합칠 브랜치 이름>`의 형태로 사용
- **Merge하기 전에 일단 다른 브랜치를 합치려고 하는, 즉 메인 브랜치로 switch 해야됨**

```
# 1. 현재 branch1과 branch2가 있고, HEAD가 가리키는 곳은 branch1 입니다.
$ git branch
* branch1
  branch2

# 2. branch2를 branch1에 합치려면?
$ git merge branch2

# 3. branch1을 branch2에 합치려면?
$ git switch branch2
$ git merge branch1
```



## 5. Git workflow

### 5.1 원격 저장소 소유권이 있는 경우 (Shared repository model)

1. 소유권이 있는 원격 저장소를 로컬 저장소로 `clone` 받음

   ```
   $ git clone https://github.com/edukyle/django-project.git
   ```

2. 사용자는 자신이 작업할 기능에 대한 `브랜치를 생성`하고, 그 안에서 `기능을 구현`

   ```
   $ git switch -c feature/login
   ```

3. 기능 구현이 완료되면, 원격 저장소에 해당 `브랜치`를 push

   ```
   $ git push origin feature/login
   ```

4. 원격 저장소에는 master와 각 기능의 브랜치가 반영됨

5. Pull Request를 통해 브랜치를 master에 반영해달라는 요청을 보냄

6. 병합이 완료되면 원격 저장소에서 병합이 완료된 브랜치는 불필요하므로 삭제

7. master에 브랜치가 병합되면, 각 사용자는 로컬의 master 브랜치로 이동

   ```
   $ git switch master
   ```

8. 병합으로 인해 변경된 원격 저장소의 master 내용을 로컬에 받아옴

   ```
   $ git pull origin master
   ```

9. 병합이 완료된 master의 내용을 받았으므로, 기존 로컬 브랜치는 삭제

   ```
   $ git branch -d feature/login
   ```



### 5.2 원격 저장소 소유권이 없는 경우 (Fork & Pull model)

- 오픈 소스 프로젝트와 같이, 자신의 소유가 아닌 원격 저장소인 경우 사용
- **원본 원격 저장소를 그대로 내 원격 저장소에 `복제` (이 행위를 `fork`라고 함)**
- 기능 완성 후 `Push는 복제한 내 원격 저장소에 진행`
- **이후 `Pull Request`를 통해 원본 원격 저장소에 반영될 수 있도록 요청**







