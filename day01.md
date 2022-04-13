# Github 특강

## 1. CLI 기초

1. 파일을 생성하는 명령어 (touch)

2. 디렉토리를 생성하는 명령어 (mkdir)

3. 현재 경로의 파일 내역들을 확인하는 명령어 (ls)
   3-1. 숨김 폴더, 파일까지 확인하는 명령어 (ls -a)

4. 파일을 이동하는 명령어 (mv)
   4-1. 만약에 이동을 지시한 디렉토리가 없다면?
   -> 이름이 변경된다

5. 삭제하는 명령어 (rm)
   5-1. 폴더를 삭제하기 위해서는?

6. 현재의 경로를 파악하는 명령어 (pwd)
   -> 절대 경로로 나의 경로를 파악할 수 있다.

   * 절대경로 : /c/Users/student/Desktop/CLI

   * 상대경로 : .. (상위경로), .(현재경로)



## 2. 마크다운 작성법 및 실습

### 2.1 마크다운 작성법

- 제목의 수준은 6단계로 이루어짐(h1~h6, \#의 갯수를 이용해 조절)
- 순서가 없는 목록(\+,\-를 이용)
  TAB, SHIFT TAB으로 내어쓰기 정도 조절 가능
- 순서가 있는 목록(1. , 2. 이용)
- 글씨체
  - 기울임 :*글자*  별표 하나 양쪽
  - 굵게 : **글자** 별표 두개 양쪽	
  - 취소선 : ~~취소선~~ 물결 두개 양쪽
- 코드는 백틱(\`) 이용
  - 인라인 코드: `인라인코드`
  - 블록 코드: (\`\`\`) 쓰고 엔터키

```java
import java.util.Scanner;
```

- 링크 작성 방법 : \[표시글자\](링크)
- 이미지 첨부 방법 : !\[대체택스트\](이미지 주소)

- 인용(\>)

> 인용문을 작성한다
>
> > 겹쳐서 사용 가능

- 표 작성 : (\|) 또는 ctrl + t 이용

| 파충류   | 포유류 | 양서류 | 조류 | 다리갯수 |
| -------- | ------ | ------ | ---- | -------- |
| 카멜레온 | ...    | ...    | ...  | 4        |

- 구분선(---)
- 원본 소스보기(ctrl + /)



### 2.2 마크다운 작성 실습

\# Java

\## 1. 개요

![](https://blog.kakaocdn.net/dn/cZsyTw/btq0u5VBWge/F7xmauYA6r8nnbXSz2vJhK/img.png)

자바(영어: Java)는 썬 마이크로시스템즈의 제임스 고슬링(James Gosling)과 다른 연구원들이 개발한 객체 지향적 프로그래밍 언어이다. 1991년 그린 프로젝트(Green Project)라는 이름으로 시작해 1995년에 발표했다.

> 객체 지향 프로그래밍은 컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러 개의 독립된 단위, 즉 "객체"들의 모임으로 파악하고자 하는 것이다.



\## 2. 특징

1. 자바 언어는 다음 5가지 핵심 목표를 지니고 있다.

   - 객체 지향 방법론을 사용해야 한다.
   - 같은 프로그램(바이트코드)이 여러 운영 체제(마이크로프로세서)에서 실행될 수 있어야 한다.
   - 컴퓨터 네트워크 접근 기능이 기본으로 탑재되어 있어야 한다.
   - 원격 코드를 안전하게 실행할 수 있어야 한다.
   - 다른 객체 지향 언어들의 좋은 부분만 가지고 와서 사용하기 편해야 한다.

2. 자바 예제

   ```java
   public class HelloWorldApp {
     public static void main(String[] args) {
       System.out.println("Hello World!");
     }
   }
   ```

3. 공식문서
   [자바 공식문서 링크](https://docs.oracle.com/javase/8/docs/api/)



## 3. Git 기초

0. 초기설정
   - git config --global user.name "유저명"
   - git config --global user.email "깃허브 메일"

1. 폴더를 저장소로 만들기

   - git init 						// 폴더 (master) 지정

   - touch README.md   // 파일만들기

2. 무대 위로 올리기 (staging area)
   - git add README.md

3. 파일 상태 확인
   - git status

4. 변경사항 기록(commits)
   - git commit -m "커밋 메세지"

5. 변경사항 log 확인
   - git log (--oneline)



## 4. Github

1. new repository 만들고 url 복사

2. Git과 Github 연결하기

   - git remote add origin '복사한url'

   - git remote -v            // 연결 확인

3. git push origin master    // Github에 변경사항 백업하기

