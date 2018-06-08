# 생활코딩 MySQL
----------------
## 데이터베이스의 목적
### 스프레드시트와 데이터베이스의 공통점과 차이점
- 공통점: 자료를 표의 형태로 표현
- 차이점(스프레드시트): 클릭으로 데이터를 조작
- 차이점(데이터베이스): 컴퓨터 언어를 통해 데이터 제어
### 데이터베이스와 웹의 관계
- 데이터베이스와 웹이 결합된 상황에서,
- 데이터베이스의 정보를 누구나 웹을 통해서 확인할 수 있다
- 누구나 웹에 자료를 작성하면 해당 자료가 데이터베이스에 저장된다
----------------
## MySQL의 구조
- 결국 정보는 표에 저장된다
- 그럼 여러 표들이 생겨나고, 많아진 표들을 또 정리해야 한다
- 서로 연관된 표들의 그룹핑 = 일종의 폴더 기능 = 데이터베이스(스키마)
- 여러 개의 스키마는 데이터베이스 서버라는 프로그램에 저장됨
- 정리하자면, 표 < 스키마 < 데이터베이스 서버
----------------
## MySQL 서버접속
- 데이터베이스 서버에 접속해보자
- 명령프롬포트(CMD)를 실행해서 다음 코드를 입력 `mysql -uroot -p`
	- Enter password: 라는 문구가 나타나면 비밀번호 입력
	- ERROR 1045 (28000): Access denied~라는 문구가 나타나면 비밀번호 틀림 → "mysql 비밀번호 분실", "mysql password recovery" 등의 키워드를 구글링하여 비밀번호 찾기
----------------
## 스키마의 사용
- 스키마 생성하기 `CREATE DATABASE opentutorials;`
- 스키마 삭제하기 `DROP DATABASE opentutorials;`
- 스키마 확인하기 `SHOW DATABASES;`
- 스키마 사용하기 `USE opentutorials;`
----------------
## SQL과 테이블의 구조
- SQL은 **S**tructured **Q**uery **L**anguage의 약자
- structured: 표의 형태로 데이터를 정리정돈
- query: 데이터베이스에 요청, 질의한다는 의미
- language: 데이터베이스와 사용자가 약속한 언어 사용
- SQL은 쉽고 중요하다
- table(표); row(행); column(열)
- 행은 데이터 자체, 열은 데이터의 타입
----------------
## 테이블의 생성
테이블 생성 명령 `CREATE TABLE topic(` 이대로 enter 치고 줄바꿈 하면서 열 생성
1. `id INT(11) NOT NULL AUTO_INCREMENT`
	- **INT(11)** 정수형으로 데이터 타입을 강제하겠다
	- **NOT NULL** 값이 없는 것을 허용하지 않겠다
	- **AUTO_INCREMENT** 자동으로 1씩 증가한다, 중복되지 않는 식별자 생성
2. `title VARCHAR(100) NOT NULL`
	- **VARCHAR(100)** 문자형으로 데이터 타입을 강제하고, 100개까지만 허용하겠다
3. `description TEXT NULL`
	- **TEXT** 긴 문자형으로 데이터 타입을 강제하겠다
	- **NULL** 값이 없는 것을 허용하겠다
4. `created DATETIME NOT NULL`
	- **DATETIME** YYYY-MM-DD HH-MM-SS로 데이터 타입을 강제하겠다
5. `author VARCHAR(30) NULL`
6. `profile VARCHAR(100) NULL`
7. `PRIMARY KEY(id)`
	- **PRIMARY KEY** 해당 열이 메인 키임을 지정
	- 중복 방지: 각각의 값이 중복되면 안 돼!라는 의미
----------------
## INSERT
- `DESC topic;` 테이블의 구조 확인 (DESC는 describe의 약자)
- `INSERT INTO topic (title,description,created,author,profile) VALUES('MySQL','MySQL is...',NOW(),'egoing','developer');`
	- 데이터 행 추가하는 방법	
	- 순서쌍에 맞게 나열할 것
- `SELECT * FROM topic;` topic 테이블 전체를 출력
	- *는 전체를 의미
## SELECT
- `SELECT (열 명) FROM (테이블 명) WHERE (행 조건식) ORDER BY (열 명) (ASC/DESC) LIMIT (개수);`
	- SELECT는 열 선택하여 출력 시 사용
	- 반드시 WHERE는 FROM 다음에 기재
	- WHERE는 행 선택, 뒤에 행의 조건식을 기재
	- ORDER BY는 정렬, 뒤에 열 명과 정렬 순서를 기재
	- **ASC** 오름차순 **DESC** 내림차순
	- LIMIT은 출력되는 개수 제한
## UPDATE
- `UPDATE (테이블 명) SET (변경 조건식) WHERE (행 조건식);`
- WHERE문 빠뜨리면 큰 재앙이 올 수 있으니 반드시 기재할 것
- 'RENAME TABLE (테이블 명) TO (새로운 테이블 명);`
## DELETE
- 'DELETE FROM (테이블 명) WHERE (행 조건식);'
----------------
## 관계형 데이터베이스의 필요성
- 중복이 있다 → 개선할 것이 있다
- 테이블끼리 관계를 맺기 때문에 유지 보수하기 쉽다
- trade-off: 직관적으로 데이터 보기 어려움, 별도의 표를 참조해야하는 불편함
- 저장은 분리해서, 읽어올 때는 합쳐서
----------------
## JOIN
- `SELECT * FROM topic LEFT JOIN author ON topic.author_id = author.id;`
	- **JOIN** 두 개의 서로 다른 테이블을 결합한다
	- **ON** 어느 공통 지점에서 결합시킬 것인지 뒤에 조건식 작성
	- 두 개의 테이블의 열 이름 중복 시, 열 이름 앞에 '(테이블 명).'을 입력한다
	- 혹은 `SELECT (테이블 명).(열 이름) AS (새로운 열 이름)`으로 지정할 수도 있다
----------------
## 인터넷과 데이터베이스
- 인터넷: 흩어져 있는 컴퓨터들끼리 만들어진 사회
- 웹: 정보를 요청하고, 요청에 응답하는 과정
- 클라이언트: 정보를 요청하는 쪽(갑)
- 서버: 정보를 제공하는 쪽(을)
- 우리가 사용한 클라이언트: `mysql`로 시작한 명령어 기반의 프로그램(MySQL Monitor)
----------------
## MySQL Client & Workbench
- MySQL Monitor: 명령어 기반 프로그램으로 어디에서나 사용할 수 있다
- MySQL Workbench: 마우스로 제어할 수 있는 GUI 기반 프로그램
- 맥락에 따라 두 프로그램을 사용하며 장점 습득하고 인지해야
- `mysql -uroot -p -hlocalhost` 클라이언트와 서버가 같은 컴퓨터일 때 -hlocalhost 기재
- 추후 스터디 방향: index, modeling, backup, cloud, programming
