# Servlet / JSP 개요

네트워크 통신 개요

- 서버는 특정한 서비스를 제공하는 컴퓨터를, 클라이언트는 이러한 서비스를 사용하는 사용자를 말함

Web 통신 구조

- webserver 정적인 부분 처리
- was 동적 페이지까지 처리

Web Server

> 사용자에게 HTML페이지나 jpg, png 같은 이미지(**정적인 부분**)를 HTTP 프로토콜을 통해 웹 브라우저에 **제공**하는 서버로 내부의 내용이 이미 만들어져 있는 정적인 요소들을 화면에 보여주는 역할을 함
>
> 정적인 페이지는 요청하는 페이지가 다 준비되어 있음

- 종류
  - Apache :
  - Window IIS :
  - NGINX :

WAS

> Web Application Server의 약자로 사용자가 요청한 서비스의 결과를 스크립트 언어 등으로 가공하여 생성한 **동적**인 페이지를 사용자에게 보여주는 역할
>
> 동적인 페이지는 준비된 데이터가 무엇이냐에 따라 보여주는 것이 달라진다고 봄

- 종류
  - tomcat :
  - wildfly :
  - jeus : 국산 WAS

서블릿 컨테이너와 JSP 컨테이너

- 서블릿 컨테이너(Servlet-Container)

  > 서블릿의 생명 주기 관리()

- JSP 컨테이너(JSP-Container)

  >

