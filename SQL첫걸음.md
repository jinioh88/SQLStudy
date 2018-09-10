# SQL첫걸음 책 정리자료.
  - 개인 정리용이라 자세한 사항은 책을 참조하길...

## 1장 데이터베이스와 SQL
### 데이터베이스
  - DBMS란 데이터베이스를 관리하는 소프트웨어로, 사용 목적은 생성성 향상과 기능성, 신뢰성 확보에 있따. 
  - SQL은 관계형 데이터베이스에서 사용한다. 
  - SQL 명령어 종류
    - DML
      - 데이터베이스에 새롭게 데이터를 추가/삭제/생신 등 데이터 조작할떄 사용. 
    - DDL
      - 데이터를 정의하는 명령어. 데이터베이스 객체를 만들거나 삭제한다.
    - DCL
      - 데이터를 제어하는 명령어.
      - 트렌젝션을 제어하는 명령과, 데이터 접근권한을 제어하는 명령이 포함되 있다. 

### 다양한 데이터베이스
  - 계층형 데이터베이스
    - 폴더와 파일 등의 계층 구조로 데이터를 저장하는 방식. 
    - 요즘은 잘 안쓴다.
  - 관계형 데이터베이스
    - 표 형식 데이터를 저장하는 형태의 데이터베이스. (2차원 데이터)
  - 객체지향 데이터베이스
    - 객체 그대로를 데이터베이스에 데이터로 저장하는 방식.
  - XML 데이터베이스
    - 태그를 이용해 마크업 문서를 작성할 수 있게 정의된 것. 
    - SQL 명령을 사용할 수 없고, 대신 XML 데이터를 검색할 떄 XQuery를 사용한다. 
  - 키-밸류 스토어(KVS)
    - 키와 값이라는 형태로 저장한다.
    - NoSQL이라는 슬로건으로부터 생겨난 데이터베이스. 열 지향 데이터베이스라고도 한다. 

### 데이터베이스 서버
  - 클라이언트 서버 모델
    - 클라이언트와 서버로 소프트웨어를 나누고, 복수의 컴퓨터 상에서 하나의 모델을 구현하는 시스템.
    - 웹 시스템에서의 클리이언트/서버
      - 웹 시스템이란 브라우저와 웹 서버로 구성된 클라이언트/서버 모델의 시스템을 말한다. 
    - RDBMS의 클래아언트/서버
      - 웹 시스템에 없었던 사용자 인증이 필요하다. 
    - SQL명령 실행
      - RDBMS에 접속하면 SQL 명령을 서버에 보낼 수 있다. 
      - 한번 데이터 베이스에 접속하면, 이를 유지해 재접속이 필요 없다. 
    - 웹 애플리케이션 구조
      - 일반적으로 웹 서버와 데이터베이스 서버의 조합으로 구축된다. 
      - 데이터 베이스에 접속하는 것은 CGI 프로그램이다. 
      - CGI 프로그램이 데이터베이스의 클라이언트가 된다. 
      - 클라이언트 <--> 웹서버 <--> CGI 프로그램 <--> DB

## 2장 테이블에서 데이터 검색
### Hello Wolrld 실행하기
  - SELECT * FROM 테이블명;  마지막에 ';'를 꼭 붙여주자.
      >   SELECT * FROM sample21;
  - select 명령문
    - '*'은 모든 열을 가져 오라는 것이다. 
  - 예약어와 데이터베이스 객체명
    - 데이터 베이스 객체명에는 예약어와 동일한 이름을 사용할 수 없다.
    - 중복도 안된다. 
    - 예약어와 데이터베이스 객체명은 대소문자를 구별하지 않는다. 
  - NULL은 데이터가 들어있지 않은 것을 의미한다. 

### 테이블 구조 참조하기
  - DESC 명령
    - mysql> desc sample21;
    - 위 명령으로 테이블에 어떤 열이 정의되어 있는지 알 수 있다. 
    - DESC 명령으로 테이블 구조를 참조할 수 있다. 
  - 자료형
    - 열에는 몇가지 속성을 지정할 수 있는데, 바로 '자료형'이라 한다. 
    - INTEGER 형
      - 수치형의 하나로 정수값을 지정한다. 
    - CHAR 형
      - 문자열의 하나로 문자열를 저장할 수 있다. 
      - 최대 길이를 지정해야 한다. ex) CHAR(10)
      - 고정된 길이로 데이터 저장. 
    - VARCHAR 형
      - 문자열을 저장할 수 있다. 
      - 최대 길이를 지정해야 한다. 
      - 데이터 크기에 맞춰 저장공간의 크기가 변경된다. (가변길이 문자열 자료형)
    - DATE 형
      - 날짜값을 저장할 수 있는 자료형이다. 
      - 2018년 09월 21일
    - TIME 형
      - 시간을 저장할 수 있는 자료형.

### 검색 조건 지정하기
  - 데이터 검색에는 열을 지정하는 방법, 행을 지정하는 방법 2가지가 있다. 
  - SELECT 열1, 열2 FROM 테이블명 FROM 조건식;
  - 행을 선택할 떄는 WHERE 구를 사용하고, 열을 선택할 때는 SELECT 구를 사용한다. 
  - select 구로 열 지정하기
      >   mysql> SELECT no, name from sample21;
    - 열의 순서는 아무 상관 없다. 중복만 안하면 된다. 
  - where 구에서 행 지정하기
    - 수많은 행 속에서 필요한 것만 검색하기 위해 where를 사용한다. 
    - 값이 서로 다른 경우 '<>'를 사용한다.
      >   mysql> select * from sample21 where no <> 2;
  - 문자열형 상수
    - 수치형은 비교의 경우 문자 그대로 사용하지만 문자열형을 비교할 떈 싱클쿼트(' ')로 둘러 싸야 한다. 
  - NULL 값 검색
    - '=' 연산자론 NULL을 검색할 수 없다. 
    - 'is NULL'을 사용하자. 

### 조건 조합하기
  - 복수 조건을 where절로 지정하는데, 조합시 and, or, not 3가지 방법을 사용할 수 있다. 
  - AND로 조합하기
    - AND는 좌우에 항목이 모두 참일 경우 참을 반환한다. 
      >   mysql> select * from sample24 where a<>0 and b<>0;  // a, b가 모두 0이 아닌경우 검색
  - OR로 조합하기
    - 어느 쪽이든 하나만 참이면 참이 된다. 
    - 좌우 비교를 합집합으로 계산할 수 있다. 
  - AND, OR 주의할 점
    - 'no'로 1 또는 2인 행을 추출할 경우 다음과 같이 써야 한다.
      >   mysql> select * from sample24 where no=1 or no=2;  // no=1 OR 2; 같이 쓰면 안된다.
    - OR 보단 AND가 우선순위가 높아 헛갈리면 괄호로 우선순위를 만들자.
  - NOT으로 조합하기
    - NOT은 단항연상자이다. 
    - 조건식의 반대 값을 반환한다. 
    - a열이 0이 아니거나 b열이 0이 아닌 행을 제외한 나머지 행을 검색
      >   mysql> select * from sample24 where not(a<>0 or b<>0);  

### 패턴 매칭에 의한 검색
  - 'LIKE' 구문으로 문자열의 일부분을 비교하는 부분검색을 할 수 있다. 
  - 열 LIKE 패턴
  - LIKE에는 메타문자 %와 _를 사용할 수 있다. 
  - '='로 비교하는 경우는 셀의 데이터 값이 완전히 동일한지 비교한다. 
  - '패턴매칭' 또는 '부분검색'은 LIKE를 사용한다. 
  - 패턴은 문자열로 지정한다. 수치형 상수는 지정할 수 없다. 
  - '%'는 임의의 문자열을 의미하고, '_'는 임의의 문자 하나를 의미한다. 
      >   mysql> select * from sample25 where text like 'SQL%';  // SQL로 시작하는 문자열을 찾는다.
  - 중간에 해당 문자열을 찾는다면 다음과 같이 쓴다.
      >   mysql> select * from sample25 where text like '%SQL%';
  - LIKE로 메타 문자 검색하기(%,_)
    - 이스케이프라는 방법으로 처리할 수 있다.  '\%', '\_'
    - '를 검색하려면 '''' 이렇게 표현한다. '이거 두개를 연속해서 표현.
    - 간단한 패턴 매칭은 LIKE로 충분하고 더 복잡한 경우는 정규 표현식을 사용하는것이 좋다. 

## 3강 정렬과 연산
### 정렬 - ORDER BY
  - select 열명 from 테이블 명 where 조건식 order by 열명
  - order by 구를 지정하면 검색 결과의 행 순서를 바꿀 수 있다. 
  - desc는 내림찻군, asc는 오름차순으로 정렬. 기본이 오름차순
  - 문자열형에 숫자를 지정하면 정렬 순서는 일반 숫자의 정렬 순서와 다르다. 

### 복수의 열을 지정해 정렬하기
  - select 열명 from 테이블 명 where 조건식 order by 열명, 열명 [ASC|DESC]...
  - NULL 값의 정렬 순서
    - 특성상 대소비교를 할수 없어 별도의 방법으로 취급한다. 
    - order by로 지정한 열에서 null 값을 가진 행은 가장 먼저 표시되거나, 가장 나중에 표시된다. 
    - MYSQL은 NULL값을 가장 작은 값으로 취급해 ASC로 정렬하면 가장 먼저 나온다. 

### 결과 행 제한하기 - LIMIT
  - select 명령에서 결과값으로 반환되는 행을 제한할 수 있다. 
  - select 열명 from 테이블명 where 조건 order by 열명 limit 행수 [offset 시작행];
  - 게시판의 경우 페이지를 나눠 표시할 때 사용된다. 
  - LIMIT은 표준이 아니라 MYSQL, PostgreSQL에서 사용할 수 있다. 
    - SQL Server에선 'TOP', Oracle에선 'ROWNUM'을 활용한다.
  - 명령어 맨 마지막에 적어야 한다. 
  - 오프셋 지정
    - 게시판 페이지를 나눌때 1~5페이지가 한 화면이고 6부터가 다음 페이지라고 할떄, '6번째 행부터'라는 표현은 LIMIT구의 OFFSET으로 지정할 수 있다.
    - 생략 가능하고 기본값은 0이다. 
    - LIMIT 뒤에 적는다. 
    - 0부터 시작함. 
    - select 열명 from 테이블명 limit 행수 offset 위치 

### 수치연산
  - select구나 where구 안에서 연산을 할 수 있다. 
  > mysql> select *, price*quantity from sample34;
  - 열의 별명
    - 식 뒤에 한칸 띄고 별명을 붙이면 된다. 예약어는 as. 생략 가능
    - 별명을 한글로 하면 오작동 하는 경우가 있어서 ""안에 쓴다. 
    - ""로 둘러싸면 데이터 베이스 객체의 이름이라 간주하고, ''로 둘러 싸면 문자열 상수로 간주한다. 
    - 객체명은 숫자로 시작 안하는게 관례
  - where구에서 연산하기 
    - price*quantity 부분을 amount 별명으로 하면 안된다. 
    > mysql> select *, price*quantity as amount from sample34 where price*quantity>2000;
  - where 구와 select 구의 내부 처리 순서
    - where구 --> select 구 의 순서로 처리돤다. 그래서 where 구에서 별명이 사용 안된다. 
  - NULL 값의 연산
    - SQL에서 NULL은 0으로 처리되지 않는다.
    - NULL+1 하면 NULL이다. 
  - order by 구에서 연산
    - order by는 서버에서 내부적으로 가장 나중에 처리되 별명을 적용할 수 있다. 
    > mysql> select *, price*quantity as amount from sample34 order by amount desc;
  - 함수
    - 연산자 외에 함수를 사용해 연산할 수도 있다. 
    - ROUND 함수
      - 반올림 할 때 사용. 
        > mysql> select amount, ROUND(amount) from sample341
      - 기본적으로 소수점 첫째 자리 기준으로 반올림 한다. 
      - round(amount,1) 이렇게 하면 소수점 둘째 자리에서 반올림함.음수 값도 쓸수 있는데 음수는 앞에 정수형에서 반올림한다. 

### 문자열 연산
  - 문자열의 결합
    - mysql : concat
    - SQL Server : '+'
    - Oracle : ||
      > mysql> select concat(quantity,unit) from sample35;
  - substring 함수
    - 문자열의 일부분을 반환. 
    - substring('20180925',1,4) --> '2014'
  - trim 함수 
    - 문자열의 앞뒤로 여분의 스페이스를 제거해 준다. 
    - 빈공간을 채운 스페이스를 제거하는데 사용할 수 있다. 
    - trim('abc   ') --> 'abc'
  - character_length
    - 문자열의 길이를 계산해 돌려준다. 
    - varchar는 가변길이라 이를 이용해 문자열의 길이를 계산할 수 있다. 
    - 'char_length'로 줄여쓸 수 있다. 
    - 'octet_length'는 문자열의 길이를 바이트 단위로 계산해 돌려준다. 

### 날짜 연산
  - SQL에서의 날짜
    - 시스템 날짜 : 하드웨어 상의 시계로 부터 실시간으로 가져오는 것. select CURRENT_TIMESTAMP 함수로 실행.
    - 날짜 서식 : 날짜 데이터를 데이터베이스에 저장할 경우 current_timestamp를 사용해 시스템 상 날짜를 저장할 수 있다. 서식을 지정할 수 도 있다. 
  - 날짜의 덧셈과 뺄셈
    - select current_date + interval 1day // 1일 후를 계산. 
    - 두날짜간 차이를 계산할 수 있다. datediff 이용.

### case 문으로 데이터 변환하기
  >
    case when 조건식1 then 식1
        [when 조선식2 then 식2...]
        [else 식3]
    end
  - 임의의 조건에 따라 독자적으로 변환 처리를 지정해 데이터를 변환하고 싶은 경우 사용한다. 
  - case문
    - 예로 null값을 0으로 간주하여 계산하고 싶은 경우. 사용자 함수로도 할 수 있지만, case 문으로도 처리할 수 있다. 
    - when 절엔 참고 ㅏ거짓을 반환하는 조건식을 기술. 만족하면 then이 실행. 
    - 가장먼저 when절의 조건을 만족하는 then 절의 처리 결과를 case 문의 결과값으로 변환한다. 
    - else는 생략 가능. 생략하면 else null로 간주.. 
    > mysql> select a , case when a is null then 0 else a end "a(null=0)" from sample37;
  - coalesce
    - null 값을 변환하는 경우 coalesce 함수를 사용하면 편하다. 
    - select a, coalesce(a,0) from sample37; // null 이 아니면 a를 출력. 
  - 숫자로 이뤄진 코드를 알아보기 더 쉽게 문자열로 변환하고 싶은 경우 case 문을 많이 이용한다. 1/2 --> 남/여
    - when a=1 then '남자' when a=2 then '여자'
    - 이렇게 문자화 하는 것을 '디코드'라 한다. 반대로 수치화 한것을 '인코드'라 부른다.   
  - case문은 '검색 case'와 '단순 case'의 두 구문으로 나뉠 수 있다. 
    - 검색 case는 case when 조건식 then 식... 구문
    - 단순 case는 case 식1 when 식2 then 식3... 구문.
      - 식1에서 when의 식2와 같은지 비교, 같으면 식3의 값이 case 문 전체의 결과값이 된다. 일치하는게 없으면 else절이 적용됨
      >  mysql> select a as "코드", case when a=1 then '남자' when a=2 then '여자' else '미정' end as "성별" from sample37; (검색 case)
      - 단순 case의 경우 case문에서 비교할 항목인 'a'를 따로 지정하므로 비교할 값만 기술하면 된다. 
      > mysql> select a as "코드", case a when 1 then '남자' when 2 then '여자' else '미정' end as "성별" from sample37;
  - case 문은 where, order by 등에서도 사용 가능하다. 
  - else를 생략하면 else null 이 자동 입력 된다. 그러므로 else는 생략 안하는게 좋다. 
  - null 판단은 a = null 이렇게 말고 a is null 이렇게 사용한다. 

## 4장 데이터 추가, 삭제, 갱신
### INSERT
  - insert into 테이블명 values(값1, 값2...);  행을 추가한다. 
  - 클라이언트에서 테이터베이스 서버로 데이터를 전송한다. 
  - 값을 저장할 열 지정하기
    - insert into 테이블명 (열1, 열2...) values(값1, 값2...);
  - NOT NULL 제약
    - NOT NULL 제약이 있을때 NULL을 입력하면 에러 발생. 
  - DEFAULT
    - 명시적으로 값을 지정하지 않은 경우 초기값을 지정한다. 
    - values(DEFAULT); values에 DEFAULT 키워드를 사용하여 지정한다. (명시적 지정 방법)
    - 해당 지정할 열에 별도로 지정하지 않는 방법 (암묵적 지정 방법)

### DELETE
  - delete from 테이블명 where 조건식
  - where절을 지정할 수 있는데 생략하면, 모든 행을 지워 버린다. 

### UPDATE
  - update 테이블명 set 열1 = 값1, 열2 = 값2,... where 조건식
  - set구에 지정한 갱신 내용은 처리 대상이 대는 모든 행에 적용된다. 
  - where구를 뺴면 조건이 일치하는 전체 행에 적용된다. 

## 5장 집계와 서브쿼리
### COUNT - 행구하기
  - count(집합);
  - 집계함수는 하나의 집합으로 부터 하나의 값을 반환한다. 
  >   select count(*) from sample51 where name='A';
  - count 인수로 열명을 지정하면 열에 한해서 행의 개수를 구한다. 
    - count만 인수로 *를 쓸 수 있다.
  - null은 집계에서 제외한다. 단 인수로 *게 오면 null 값도 다른것을 참조해 카운트 된다. 
  - select distinct count(name) from sample51; 하면 안됨.  count가 먼저 계산 되서...
    - 집계 함수의 인수로 distinct를 사용한 수식을 지정하자. 
    - select count(distinct name) from sample51; 

### COUNT 이외의 집계함수
  - sum으로 잡합의 합을 구할 수 있다. 수치형만 집계 된다. null 값은 무시한다. 
  >  mysql> select sum(quantity) from sample51;
  - avg로 편하게 평균을 구할 수 있다. null 빼고 평균 구하는데, null 포함하려면 case를 사용한다. 
    - select avg(case when quantity is null then 0 else quantity end) from sample51;
  >  mysql> select avg(quantity) from sample51;

### GROUP BY
  - 