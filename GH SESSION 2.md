## 정렬과 연산
- CONCAT 원하는 문자열을 결합하는 함수
  - 사용 예시: SELECT CONCAT(열 명1, 열 명2) FROM 테이블 명;
- SUBSTRING 문자열의 일부를 반환하는 함수
  - 사용 예시: SUBSTRING(문자열, 시작인덱스, 길이) *인덱스 1부터
- CHARACTER_LENGTH 문자열의 길이를 수치로 반환하는 함수
  - 사용 예시: SELECT CHAR_LENGTH 열 명 FROM 테이블 명;
- OCTET_LENGTH 문자열 데이터를 바이트 단위로 계산해 반환하는 함수 (인코드 방식)
- CURRENT_TIMESTAMP 현재 날짜와 시간을 반환하는 시스템 날짜 함수
- CURRENT_DATE + INTERVAL 1 DAY 날짜를 연산해 시스템 날짜의 1일 후를 검색
- DATEDIFF('날짜1', '날짜2') 날짜형 간의 뺄셈
- CASE 약어나 코드를 읽기 쉬운 값으로 바꿔줄 때 사용, 데이터를 범주화
  - 사용 예시: CASE 열 명/ WHEN 조건1 THEN 값1/ WHEN 조건2 THEN 값2/ ELSE 값3/ END
- ELSE 생략 시, ELSE NULL이 된다
---
## 데이터의 추가, 삭제, 갱신
- INSERT INTO 테이블 명(열 명1, 열 명2, ...) VALUES(데이터1, 데이터2, ...);
- DELETE FROM 테이블 명 WHERE 조건식;
- UPDATE 테이블 명 SET 열 명1 = 데이터1, 열 명2 = 데이터2, ... WHERE 조건식;
---
