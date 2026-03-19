<h1 id="sql의-개념">SQL의 개념</h1>
<br />

<h3 id="ddldata-define-language-데이터-정의어">DDL(Data Define Language, 데이터 정의어)</h3>
<h4 id="schema-domain-table-view-index를-정의하거나-변경-삭제할-때-사용하는-언어를-뜻한다">SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의하거나 변경, 삭제할 때 사용하는 언어를 뜻한다.</h4>
<h4 id="명령어로는-create-alter-drop이-있다">명령어로는 CREATE, ALTER, DROP이 있다.</h4>
<h4 id="create는-schema-domain-table-view-index를-정의하는-명령어다">CREATE는 SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의하는 명령어다.</h4>
<h4 id="alter는-table의-정의를-변경하는데-사용한다">ALTER는 TABLE의 정의를 변경하는데 사용한다.</h4>
<h4 id="drop은-schema-domain-table-view-index를-삭제하는데-사용한다">DROP은 SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 삭제하는데 사용한다.</h4>
<br />

<h3 id="dmldata-manipulation-language-데이터-조작어">DML(Data Manipulation Language, 데이터 조작어)</h3>
<h4 id="데이터베이스-사용자가-응용-프로그램이나-질의어를-통해-데이터를-처리하는데-사용되는-언어다">데이터베이스 사용자가 응용 프로그램이나 질의어를 통해 데이터를 처리하는데 사용되는 언어다.</h4>
<h4 id="명령어로는-selete-insert-delete-update가-있다">명령어로는 SELETE, INSERT, DELETE, UPDATE가 있다.</h4>
<h4 id="selete는-테이블에서-조건에-맞는-튜플을-검색하는-용도다">SELETE는 테이블에서 조건에 맞는 튜플을 검색하는 용도다.</h4>
<h4 id="insert는-테이블에-새-튜플을-삽입하는-용도다">INSERT는 테이블에 새 튜플을 삽입하는 용도다.</h4>
<h4 id="delete는-테이블에서-조건에-맞는-튜플을-삭제하는-용도다">DELETE는 테이블에서 조건에 맞는 튜플을 삭제하는 용도다.</h4>
<h4 id="update는-테이블에서-조건에-맞는-튜플의-내용을-변경하는-용도다">UPDATE는 테이블에서 조건에 맞는 튜플의 내용을 변경하는 용도다.</h4>
<br />

<h3 id="dcldata-control-language-데이터-제어어">DCL(Data Control Language, 데이터 제어어)</h3>
<h4 id="데이터의-보안-무결성-회복-병행-수행-제어-등을-정의하는데-쓰는-언어다">데이터의 보안, 무결성, 회복, 병행 수행 제어 등을 정의하는데 쓰는 언어다.</h4>
<h4 id="명령어로는-commit-rollback-grant-revoke가-있따">명령어로는 COMMIT, ROLLBACK, GRANT, REVOKE가 있따.</h4>
<h4 id="commit은-명령에-의해-수행된-결과를-물리적-저장소에-저장하고-데이터베이스-조작-작업이-정상적으로-완료되었음을-관리자에게-알려준다">COMMIT은 명령에 의해 수행된 결과를 물리적 저장소에 저장하고 데이터베이스 조작 작업이 정상적으로 완료되었음을 관리자에게 알려준다.</h4>
<h4 id="rollback은-데이터베이스-조작-작업이-비정상적으로-종료되었을-때-원래-상태로-복구하는-것을-의미한다">ROLLBACK은 데이터베이스 조작 작업이 비정상적으로 종료되었을 때, 원래 상태로 복구하는 것을 의미한다.</h4>
<h4 id="grant는-사용자에게-권한을-부여하는-것을-말한다">GRANT는 사용자에게 권한을 부여하는 것을 말한다.</h4>
<h4 id="revoke는-사용자에게-권한을-취소하는-것을-말한다">REVOKE는 사용자에게 권한을 취소하는 것을 말한다.</h4>
<br />
<br />

<h1 id="ddl">DDL</h1>
<br />

<h3 id="create-table">CREATE TABLE</h3>
<h4 id="테이블을-정의하는-명령문이다-테이블에-포함될-모든-속성에-대해-속성명-데이터-타입-기본값-note-null-여부를-정한다-또한-기본키-대체키-외래키-제약조건제약조건의-조건식-등을-정한다">테이블을 정의하는 명령문이다. 테이블에 포함될 모든 속성에 대해 속성명, 데이터 타입, 기본값, NOTE NULL 여부를 정한다. 또한 기본키, 대체키, 외래키, 제약조건(+제약조건의 조건식) 등을 정한다.</h4>
<br />

<h3 id="alter-table">ALTER TABLE</h3>
<h4 id="테이블에-대한-정의를-변경하는-명령문">테이블에 대한 정의를 변경하는 명령문.</h4>
<p>-- 추후수정(0319~0320 예정)</p>