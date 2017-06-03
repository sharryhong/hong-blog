---
title: Servlet & 자바 웹 애플리케이션 구조
date: 2017-06-03 23:19:00
categories: [Back-End, Java]
tags: [Servlet]
---

![Java Servlet](/image/java-servlet.png)

**웹 애플리케이션의 구성요소** 3가지는
1) 서블릿(servlet) : 클라이언트의 요청을 처리합니다.
2) 필터(filter) : 서블릿을 실행하기 전이나 후에 작업을 수행합니다.
3) 리스너(listener) : 서블릿 컨테이너의 특정 상황(event)에서 작업하는 객체입니다.

이 중 서블릿(servlet)에 대해 알아보겠습니다.

### 서블릿이란?
서버에서 실행하는 작은 프로그램 조각이라는 의미로, 동적 자원(Dynamic Resource)을 생성합니다.

이를 위해 **자바 웹 애플리케이션 구조**(Java Web Application Architecture)를 간단히 살펴보면,
![자바 웹 애플리케이션 구조 - 그림 죄송합니다 ^^;; 껄껄](/image/java-servlet-1.png)

위 그림 중 **HTTP Server + Servlet Container = WAS(Web Application Server)**입니다.
톰켓 서버도 두 기능을 탑재하고 있지만, 대체로 HTTP Server는 좀 더 성능이 뛰어난 Apache 등으로 대체해서 사용합니다.

**HTTP Server에서는 웹 애플리케이션의 정적 자원(Static Resource)** 즉, HTML, CSS, JavaScript, gif등 변하지 않는 자원을 클라이언트 요청에 따라 그대로 읽어서 전달해줍니다.

반면 **Servlet Container는 웹 애플리케이션의 동적 자원(Dynamic Resource)** 즉, JSP, Servlet등을 생성합니다.
오늘의 주인공 서블릿이 등장했습니다. :)
쉽게 말하면, 웹 애플리케이션을 구성하는 로그인, 로그아웃, 장바구니 등 이 모두가 하나의 서블릿입니다.

서블릿을 생성하기 위해서는 javax.servlet.Servlet 인터페이스 규칙에 따라 구현해야합니다.  
서블릿을 만드는 3가지 방법은 다음 포스팅으로.. ^^
