---
title: JDBC(Java Database Connectivity)
date: 2017-06-04 14:29:07
categories: [Back-End, Java]
tags: [Servlet]
---

![JDBC](/image/java-jdbc.png)

#### 관련 용어
**ODBC**(Open Database Connectivity)
데이터베이스에 접근하기 위한 소프트웨어의 표준 규격
MySQL, Oracle, MS-SQL 등 DBMS사 마다 달랐던 API를 통일하여 사용하고자 만든 규격입니다.

**JDBC**(Java Database Connectivity)
자바에서 데이터베이스에 접속할 수 있도록 하는 자바 API
데이터베이스에서 자료를 쿼리하거나 업데이트하는 방법을 제공합니다.

**Type4 JDBC Driver = DBMS Protocol Driver**
개발자들이 가장 많이 사용하는 방법으로 JDBC Driver는 DBMS와 직접 소켓 통신을 합니다.
각 DBMS사의 전용 프로토콜로 소켓 통신을 하므로, Vender전용 드라이버로서 별도 다운로드가 필요합니다.

#### MySQL JDBC Type 4 드라이버 다운로드
1) [www.mvnrepository.com](www.mvnrepository.com) 에서 mysql을 검색합니다.
  내컴퓨터 mysql버전에 따라 다운로드 받아야 합니다.
  mysql버전 명령창에서 확인 `>mysql --version `   `5.7.17버전`

2) MySQL Connector/J의 Gradle 의존 라이브러리 정보를 복사합니다.
  mysql버전에 해당하는 MySQL Connector/J » 5.1.42 의 Gradle탭 내용을 복사합니다.

3) build.gradle의 dependencies {} 블록에 붙여 넣습니다.
  ```
  dependencies {
    compile group: 'mysql', name: 'mysql-connector-java', version: '5.1.42'
  }
  ```

4) 명령창 해당 프로젝트 폴더에서 gradle 명령을 실행합니다.
   `> gradle eclipse`     <== 이클립스 설정 파일(.classpath, .project 등)을 갱신합니다.

5) 이클립스에서 프로젝트 폴더를 "Refresh" 합니다.

6) 드라이버 라이브러리 파일(mysql-connector-java-5.1.42.jar)에 있는 클래스를 로딩해 봅니다.
  ```
  public class Test01 {
    public static void main(String[] args) throws Exception {
      // MySQL JDBC 드라이버의 정보를 다루는 객체를 생성합니다.
      // => 이 객체가 있어야만 MySQL DBMS에 연결할 수 있습니다.
      com.mysql.jdbc.Driver driver = new com.mysql.jdbc.Driver();
    }
  }
  ```
