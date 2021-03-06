# TDD-nodejs

# 테스트 주도 개발 (TDD)

## 1. Mocha, should, superTest

### 1. Mocha

1. 모카는 테스트 코드를 돌려주는 테스트 러너
2. 테스트 수트: 테스트 환경으로 모카에서는 describe()로 구현한다.
3. 테스트 케이스: 실제 테스트를 말하며 모카에선 it()으로 구현한다.

### 2. should

1. 노드 assert말고 서드파트 라이브러리를 사용하라
2. 슈드는 검증 라이브러리이다.
3. 가독성이 높은 코드를 만들 수 있다.

### 3. superTest

1. 단위 테스트 : 함수의 기능 테스트.
2. 통합 테스트 : API의 기능 테스트.
3. 슈퍼 테스트는 익스프레스 통함 테스트용 라이브러리다
4. 내부적으로 익스프레스 서버를 구동시켜 실제 요청을 보낸뒤 결과를 검증한다.

# NodeJs

### 1 v8엔진

1. 브라우저 밖에서 자바스크립트 코드를 실행할 수 있다.
2. 크롭에서 사용하는 v8엔진을 사용한다.
3. 이벤트 기반의 비동기 I/O 프레임 워크
4. CommanJS를 구현한 모듈 시스템

### 2. 비동기 I/O 프레임 워크

1. 이벤트 루프(싱글스레드)
2. Non-bloacking Worker 이벤트 루프에서 전달 받은 무거운 일을 수행한다.
   - 그 후 이벤트 큐로 보내고
   - 이벤트 루프가 돌고 클라이언트로 결과를 보낸다.

### 3. 모듈 시스템

1. window.module 이런식으로 모듈을 사용했다......
2. 노드는 파일형태로 모듈을 관리할 수 있는 CommonJS(파일접근 가능)로 구현

   - 기본 모듈

### 4. 비동기 세계

1. 노드는 기본적으로 비동기로 동작함

# Express

1. nodejs 프레임워크
2. 어플리케이션
3. 미들웨어
4. 라우팅
5. 요청객체
6. 응답객체

### 어플리케이션

1. 익스프레스 인스턴스를 어플리케이션이라 한다.
2. 서버에 필요한 기능인 미들웨어를 어플리케이션에 추가한다.
3. 라우팅 설정을할 수 있다.
4. 서버를 요청 대기 상태로 만들수 있다.

### 미들웨어

1. 미들웨어는 함수들의 연속이다.
2. 일반 미들웨어 vs 에러 미들웨어
3. 미들웨어 실행순서
   - app.use를 사용하여 미들웨어 등록
   - next() 함수를 꼭 호출 해주어야 한다.

### 라우팅

1. 요청 url에 대해 적정할 핸들러 함수로 연결 해주는 기능을 라우팅이라고 부른다.
2. 어플리케이션의 get(), post() 메소드로 구현할 수있다.
3. 라우팅을 위한 전용 Router 클래스를 사용할 수 있다.

### 요청 객체

1. 클라이언트 요청 정보를 담은 객체를 요청(Request)객체라고 한다.
2. http모듈의 request객체를 래핑한 것이다.
3. req.params(), req.body(), req.query()메소드를 주로 사용한다.

### 응답 객체

1. 클라이언트 요청 정보를 담은 객체를 응답(Response)객체라고 한다.
2. http모듈의 response 래핑한 것이다.
3. req.send(), req.status(), req.json()메소드를 주로 사용한다.

# Http

1. 모든 자원은 명사로 식별한다.
2. HTTP 경로로 자원을 요청한다.

   - GET
   - POST
   - PUT
   - DELETE

3. 상태 코드
   - 2XX: 자, 여기있어
   - 200: 성공(success), GET, PUT
   - 201: 작성됨(created), POST
   - 204: 내용 없음 (No Conent), DELETE
   - 4XX: 니가 문제임
   - 400: 잘못된 요청 (Bad Request)
   - 401: 권한 없음 (Unauthorized)
   - 404: 찾을 수 없음 (Not found)
   - 409: 충돌 (Conflict)
   - 5XX: 내가 문제임
   - 500: 서버 에러 (Interel server error)

# 첫 API 만들기

1. 성공
   - 유저 객체를 담은 배열로 응답한다.
   - 최대 limit 갯 수만큼 응답한다.
2. 실패
   - limit이 숫자형이 아니면 400을 응답한다.
   - offset이 숫자형이 아니면 400을 응답한다.

# 데이터 베이스

### SqlLite3 사용 해당 디비는 파일형 데이터 베이스입니다.

### SQL

1. insert users ('name') values ('alice');
2. select \* from users;
3. update users set name = 'bek' where is =1 ;
4. delete from users where id =1;

### ORM

1. 데이터베이스를 객체로 추상화해 논 것을 ORM(Object Relational Mapping)
2. 쿼리를 직접 작성하는 대신 ORM의 메소드로 데이터 관리할 수 있는것이 장점이다.
3. 노드에서는 Sequelize를 많이 사용한다.

4. insert users ('name') values ('alice');
   - User.create({name:'alice'});
5. select \* from users;
   - User.findAll()
6. update users set name = 'bek' where is =1 ;
   - User.update({name:'beck'},{where:{id:1}});
7. delete from users where id =1;
   - User.destroy({where:{id:1}})

### Model

1. 데이터베이스 테이블을 ORM으로 추상화한것을 모델이라고 한다.
   - sequelize.define(): 모델 정의
   - sequelize.sync():데이터베이스 연동
