<h1 id="프로시저procedure">프로시저(Procedure)</h1>
<br />

<h3 id="1-프로시저의-개요">1. 프로시저의 개요</h3>
<h4 id="절차형-sql를-활용해-특정-기능을-수행하는-일종의-트랜잭션-언어다">절차형 SQL를 활용해 특정 기능을 수행하는 일종의 트랜잭션 언어다.</h4>
<h4 id="호출을-통해-실행되어-미리-저장해놓은-sql-작업을-수행하며-시스템의-일일-마감-작업-일괄-작업-등에-주로-사용된다">호출을 통해 실행되어 미리 저장해놓은 SQL 작업을 수행하며, 시스템의 일일 마감 작업, 일괄 작업 등에 주로 사용된다.</h4>
<br />

<h3 id="프로시저-생성실행제거">프로시저 생성/실행/제거</h3>
<h4 id="생성의-경우-create-procedure-명령어를-이용해-생성한다">생성의 경우, CREATE PROCEDURE 명령어를 이용해 생성한다.</h4>
<h4 id="실행의-경우-execute-명령어-또는-call-명령어를-이용해-생성한다">실행의 경우, EXECUTE 명령어 또는 CALL 명령어를 이용해 생성한다.</h4>
<h4 id="제거의-경우-drop-procedure-명령어를-사용해-제거한다">제거의 경우, DROP PROCEDURE 명령어를 사용해 제거한다.</h4>
<h4 id="예문은-다음과-같다">예문은 다음과 같다.</h4>
<pre><code>-- 1. 프로시저 생성 (CREATE PROCEDURE)
-- 특정 부서(dept_id)의 직원 정보를 조회하는 프로시저를 생성합니다.
DELIMITER //
CREATE PROCEDURE GetEmployeesByDept(IN p_dept_id INT)
BEGIN
    SELECT employee_id, employee_name, job_title
    FROM Employees
    WHERE department_id = p_dept_id;
END //
DELIMITER ;


-- 2. 프로시저 실행 (CALL 또는 EXECUTE)
-- 생성된 프로시저에 부서 ID '10'을 전달하여 실행합니다.

-- MySQL, MariaDB, PostgreSQL 등의 경우:
CALL GetEmployeesByDept(10);

-- SQL Server (MSSQL) 등의 경우:
EXECUTE GetEmployeesByDept @p_dept_id = 10;
-- (단축어인 EXEC를 사용할 수도 있습니다: EXEC GetEmployeesByDept 10;)


-- 3. 프로시저 제거 (DROP PROCEDURE)
-- 더 이상 사용하지 않거나 수정이 필요한 경우 프로시저를 삭제합니다.
DROP PROCEDURE GetEmployeesByDept;</code></pre><br />
<br />

<h1 id="트리거trigger">트리거(Trigger)</h1>
<br />

<h3 id="1-트리거의-개요">1. 트리거의 개요</h3>
<h4 id="데이터베이스-시스템에서-데이터의-삽입insert-갱신update-삭제delete-등의-이벤트가-발생할-때마다-자동으로-수행되게-하는-절차형-sql이다">데이터베이스 시스템에서 데이터의 삽입(Insert), 갱신(Update), 삭제(Delete) 등의 이벤트가 발생할 때마다 자동으로 수행되게 하는 절차형 SQL이다.</h4>
<h4 id="데이터-변경-및-무결성-유지-로그-메시지-출력-등의-목적으로-사용되며-데이터베이스에-저장된다">데이터 변경 및 무결성 유지, 로그 메시지 출력 등의 목적으로 사용되며, 데이터베이스에 저장된다.</h4>
<br />

<h3 id="2-트리거의-구성">2. 트리거의 구성</h3>
<h4 id="선언-이벤트-시작-종료로-구성되며-시작과-종료-사이에는-제어-sql-예외가-포함된다">선언, 이벤트, 시작, 종료로 구성되며 시작과 종료 사이에는 제어, SQL 예외가 포함된다.</h4>
<pre><code>DELIMITER //

-- 1. 트리거 생성 및 이름 지정
CREATE TRIGGER AfterEmployeeInsert
-- 2 &amp; 3. 트리거 시점 및 이벤트: INSERT 작업이 성공적으로 끝난 '후'
AFTER INSERT 
-- 4. 적용 대상 테이블
ON Employees 
-- 5. 실행 단위: 추가되는 각 행마다 아래 로직을 실행
FOR EACH ROW 
-- 6. 트리거 본문 시작
BEGIN
    -- NEW 키워드를 사용하여 방금 추가된 행의 employee_id 값을 가져옵니다.
    INSERT INTO Audit_Log (action_type, target_employee_id, action_time)
    VALUES ('INSERT', NEW.employee_id, NOW());
END //
-- 트리거 본문 종료

DELIMITER ;</code></pre><br />

<h3 id="3-트리거의-생성제거">3. 트리거의 생성/제거</h3>
<h4 id="생성은-create-trigger-명령어로-시작한다">생성은 CREATE TRIGGER 명령어로 시작한다.</h4>
<h4 id="제거는-drop-trigger-명령어로-제거한다">제거는 DROP TRIGGER 명령어로 제거한다.</h4>
<br />
<br />

<h1 id="사용자-정의-함수">사용자 정의 함수</h1>
<br />

<h3 id="1-사용자-정의-함수의-개요">1. 사용자 정의 함수의 개요</h3>
<h4 id="sql을-사용하여-일련의-작업을-연속적으로-처리하지만-프로시저와는-다르다">SQL을 사용하여 일련의 작업을 연속적으로 처리하지만 프로시저와는 다르다.</h4>
<h4 id="종료-시-처리-결과를-return을-통해-단일값으로-반환하는-절차형-sql이다-출력-파라미터가-없다">종료 시 처리 결과를 RETURN을 통해 단일값으로 반환하는 절차형 SQL이다. 출력 파라미터가 없다.</h4>
<h4 id="프로시저를-호출할-수-없으며-sum-avg등의-내장-함수처럼-dml문에서-반환값을-활용하기-위한-용도로-사용된다">프로시저를 호출할 수 없으며, SUM(), AVG()등의 내장 함수처럼 DML문에서 반환값을 활용하기 위한 용도로 사용된다.</h4>
<br />

<h3 id="2-사용자-정의-함수의-생성실행제거">2. 사용자 정의 함수의 생성/실행/제거</h3>
<h4 id="생성의-경우-create-function-명령어를-사용해-생성한다">생성의 경우, CREATE FUNCTION 명령어를 사용해 생성한다.</h4>
<h4 id="실행의-경우-select-insert-delete-update-등의-dml문의-호출에-의해-실행된다">실행의 경우, SELECT, INSERT, DELETE, UPDATE 등의 DML문의 호출에 의해 실행된다.</h4>
<h4 id="제거의-경우-drop-function-명령어를-사용해-제거한다">제거의 경우, DROP FUNCTION 명령어를 사용해 제거한다.</h4>
<pre><code>-- 1. 사용자 정의 함수 생성 (CREATE FUNCTION)
-- 원래 가격(price)과 할인율(discount_rate)을 받아 할인가를 정수로 반환하는 함수입니다.
DELIMITER //
CREATE FUNCTION CalculateDiscount(original_price INT, discount_rate DECIMAL(5,2))
RETURNS INT  -- 반환할 데이터의 타입을 지정합니다.
DETERMINISTIC -- 동일한 입력에는 항상 동일한 결과를 반환함을 명시합니다.
BEGIN
    DECLARE final_price INT; -- 결과를 담을 변수 선언
    SET final_price = original_price - (original_price * (discount_rate / 100));
    RETURN final_price; -- 최종 계산된 값을 반환합니다.
END //
DELIMITER ;


-- 2. 사용자 정의 함수 실행 (SELECT, INSERT 등의 DML문에서 호출)
-- Products 테이블을 조회하면서, 생성한 함수를 이용해 10% 할인가를 함께 출력합니다.
SELECT 
    product_name, 
    price AS original_price, 
    CalculateDiscount(price, 10) AS discounted_price_10pct
FROM Products;


-- 3. 사용자 정의 함수 제거 (DROP FUNCTION)
-- 더 이상 사용하지 않거나 수정이 필요한 함수를 삭제합니다.
DROP FUNCTION CalculateDiscount;</code></pre><br />
<br />

<h1 id="dbms-접속-기술">DBMS 접속 기술</h1>
<br />

<h3 id="1-jdbcjava-database-connectivity">1. JDBC(Java DataBase Connectivity)</h3>
<h4 id="java-언어로-데이터베이스에-접속하고-sql문을-수행할-때-사용되는-표준-api">JAVA 언어로 데이터베이스에 접속하고, SQL문을 수행할 때 사용되는 표준 API.</h4>
<br />

<h3 id="2-odbcopen-database-connectivity">2. ODBC(Open DataBase Connectivity)</h3>
<h4 id="데이터베이스에-접근하기-위한-표준-개방형-api-언어에-상관-없이-사용-가능">데이터베이스에 접근하기 위한 표준 개방형 API. 언어에 상관 없이 사용 가능.</h4>
<br />

<h3 id="3-mybatis">3. MyBatis</h3>
<h4 id="jdbc-코드를-단순화하여-사용할-수-있는-sql-mapping-기반-오픈-소스-접속-프레임워크">JDBC 코드를 단순화하여 사용할 수 있는 SQL Mapping 기반 오픈 소스 접속 프레임워크.</h4>
<br />

<h3 id="4-동적-sqldynamic-sql">4. 동적 SQL(Dynamic SQL)</h3>
<h4 id="개발-언어에-삽입되는-sql-코드를-문자열-변수에-넣어-처리하는-것을-말한다-조건에-따라-sql-구문을-동적으로-변경하여-처리할-수-있으며-사용자로부터-sql문의-일부-또는-전부를-입력받아-실행이-가능하낟">개발 언어에 삽입되는 SQL 코드를 문자열 변수에 넣어 처리하는 것을 말한다. 조건에 따라 SQL 구문을 동적으로 변경하여 처리할 수 있으며, 사용자로부터 SQL문의 일부 또는 전부를 입력받아 실행이 가능하낟.</h4>
<h4 id="정적-sql에-비해서는-느리지만-상황에-따라-다양한-조건을-넣는-등-유연한-개발이-가능하게-해준다">정적 SQL에 비해서는 느리지만 상황에 따라 다양한 조건을 넣는 등, 유연한 개발이 가능하게 해준다.</h4>
<br />