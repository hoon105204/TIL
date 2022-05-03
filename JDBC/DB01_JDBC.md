# JDBC(Java DataBase Connectivity)

- 자바에서 데이터베이스에 접근할 수 있게 해주는 Programming API

<img src=".\image\DB01_01JDBC.png" alt="DB03_01JDBC" style="zoom:67%;" />

**JDBC 사용 객체**

- DriverManger

  데이터 원본에 JDBC 드라이버를 통하여 커넥션을 만드는 역할
  Class.forName() 메서드를 통해 생성되며 반드시 예외처리를 해야 함
  직접 객체 생성이 불가능하고 getConnection() 메서드를 사용하여 객체 생성 가능

  ```java
  Class.forName("com.mysql.jdbc.Driver");
  ```

- Connection
  특정 데이터 원본과 연결된 커넥션을 나타내며 Statement 객체를 생성할 때도
  Connection 객체를 사용하여 createStatement() 메서드를 호출하여 생성
  SQL 문장을 실행시키기 전에 우선 Connection 객체가 있어야함

  ```java
  String url = "jdbc:mysql://localhost/multi";
  String user = "root";
  String pw = "1234";
  Connection con = DriverManager.getConnection(url, user, pw);
  ```

- Statemsnet
  Connection 객체에 의해 프로그램에 리턴되는 객체에 의해 구현되는 일종의 메서드 집합 정의
  Connection 클래스의 createStatement() 메서드를 호출하여 얻어지며, 생성된 Statement 객체로 질의문장을 String 객체에 담아 인자로 전달하여 excuteQuery() 메서드를 호출하여 SQL질의 수행

  ```java
  try{
      String query = "SELECT ID, LAST_NAME FROM EMP";
      stmt = conn.createStatement();
      rset = stmt.executeQuery(query);
  } catch(SQLExceptione){
      e.printStackTrace();
  }
  ```

- **PreparedStatement** (가장 많이 씀)
  Connection 객체의 preparedStatement() 메서드를 사용하여 객체 생성
  SQL 문장이 미리  컴파일 되고 실행 시간동안 인수 값을 위한 공간을 확보한다는 점에서 Statement와 다름

  ```java
  try{
      String query = "INSERT INTO MEMBER VALUES(?, ?)";
      pstmt = conn.preparedStatement(query);
      pstmt.setString(1, id);
      pstmt.setString(2, password);
  } catch(SQLExceptione){
      e.printStackTrace();
  }
  ```

- ResultSet
  SELECT문을 사용한 질의 성공 시 Result Set 반환
  SQL 질의에 의해 생성된 테이블을 담고 있으며 커서(cursor)로 특정 행에 대한 참조 조작
  <img src=".\image\DB01_02ResultSet.png" alt="DB01_02ResultSet" style="zoom:67%;" />

**JDBC 코딩 절차**

1. Driver 등록
2. DBMS 연결
3. Statement 생성
4. SQL 전송
5. 결과 받기
6. 닫기(객체 반환)

```java
public class JDBCTest01 {

	public static void main(String[] args) throws ClassNotFoundException, SQLException {
		// 1. Driver 등록
		Class.forName("com.mysql.jdbc.Driver");
		
		// 2. DBMS와 연결 (Connection 개체 만든다)
		String url = "jdbc:mysql://localhost/multi"; // 어디에 있는 mysql 접속하겠다
		String user = "root";
		String pw = "1234";
		
		Connection con = DriverManager.getConnection(url, user, pw);
		
		// 3. 쿼리 준비
		String sql = "SELECT * FROM EMPLOYEE"; // 세미콜론은 빼야함
		
		Statement stmt = con.createStatement(); // sql.Statement import 해야함
		
		// 4. 쿼리 실행 및 결과 리턴
		ResultSet rs = stmt.executeQuery(sql);
		
		while(rs.next()) {
			System.out.println(rs.getInt(1)+" "+rs.getString(2)+" "+rs.getInt("SALARY")); 
		}
		
		// 5. DB 종료 - 열었던 순서 역순으로
		rs.close();
		stmt.close();
		con.close();
```

