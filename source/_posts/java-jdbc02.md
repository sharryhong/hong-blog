---
title: JDBC 프로그래밍 & java.sql 패키지
date: 2017-06-04 22:23:33
categories: [Back-End, Java]
tags: [JDBC]
---

![JDBC](/image/java-jdbc.png)

## java.sql 패키지의 주요 인터페이스 (mysql의 경우)
`java.sql.Driver` (=> 구현 com.mysql.jdbc.Driver 클래스)
=> JDBC Driver 정보를 제공하는 기능
=> DBMS와의 연결을 관리하는 객체를 리턴하는 기능

`java.sql.Connection` (=> 구현 com.mysql.jdbc.ConnectionImpl 클래스)
=> DBMS와 연결을 수행하는 기능
=> DBMS에 SQL을 전달할 객체를 리턴하는 기능

`java.sql.Statement` (=> 구현 com.mysql.jdbc.StatementImpl 클래스)
=> SQL을 MySQL 형식에 맞춰서 변환한 다음 서버에 보내는 기능
=> 서버가 보낸 결과를 다룰 객체를 리턴하는 기능
=> executeQuery() : SELECT 문 실행
=> executeUpdate() : INSERT, UPDATE, DELETE 등 DML, DDL 명령문 실행
=> executeBatch() : 여러 개의 SQL문을 실행할 때 사용
                    SELECT, INSERT, UPDATE, DELETE 등 모든 SQL 명령문 실행가능

`java.sql.ResultSet` (=> 구현 com.mysql.jdbc.ResultSetImpl 클래스)
=> DBMS 서버에서 SELECT를 실행한 후 생성된 결과를 가져오는 기능
=> next()
      서버에서 한 개의 레코드를 가져옴
      정상적을 가져왔으면 true를 리턴,
      가져올 레코드가 없으면 false를 리턴
=> getXxx(컬럼 번호 또는 컬럼명)
      서버에서 가져온 레코드의 컬럼 값을 꺼내는 메서드
      컬럼의 타입에 따라 호출하는 메서드가 다름
      숫자 -> getInt()
      문자열 -> getString()
      날짜 -> getDate() 등

## JDBC 프로그래밍

> 예외처리, 특정 DBMS에 종속되는 것을 막는 등의 코드 리펙토링이 필요하지만, 기본 개념을 위해 작성하였습니다.

#### 1) MySQL JDBC 드라이버의 정보를 다루는 객체를 생성합니다.
```
com.mysql.jdbc.Driver mysqlDriver = new com.mysql.jdbc.Driver();
```
이 객체가 있어야만 MySQL DBMS에 연결할 수 있습니다.
`com.mysql.jdbc.Driver`는 `java.sql.Driver` 인터페이스에 따라 만들어져 있습니다.

#### 2) MySQL JDBC 드라이버를 "드라이버 관리자"에 등록합니다.
```
DriverManager.registerDriver(mysqlDriver);
```

#### 3) 드라이버 관리자를 통해 DBMS와 연결합니다.
```
java.sql.Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/dbname", /* 연결할 DBMS와 데이터베이스 정보 */
    "userid",
    "password");
```

#### 4) SQL을 실행할 Statement 객체 얻기
```
java.sql.Statement stmt = con.createStatement();
```
java.sql.Statement 규격에 따라 만든 객체를 리턴합니다.
Statement 객체가 SQL 문을 DBMS에 보내는 일을 합니다.

#### 5) SELECT SQL문을 DBMS에 보냅니다.
```
java.sql.ResultSet rs = stmt.executeQuery("select mno, name, tel, email from memb");
```
executeQuery() : 서버가 SELECT를 실행한 후 준비한 결과 값을 가져오는 객체를 리턴하는데, java.sql.ResultSet 규격에 따라 만들어져 있습니다.

#### ResultSet 객체를 통해 서버에 결과를 한 개씩 가져옵니다. (next() 메서드)
```
while (rs.next()) {
  System.out.printf("%d, %s, %s, %s\n",
      rs.getInt("mno"),
      rs.getString("name"),
      rs.getString("tel"),
      rs.getString("email"));
}
```

#### 6) 지금까지 사용한 JDBC 관련 객체의 자원을 생성된 역순으로 해제시킵니다.
```
rs.close();      // ResultSet 자원 해제
stmt.close();    // Statement 자원 해제
con.close();     // DBMS와 연결을 끊고 싶다면 Connection의 close()를 호출합니다.
```
