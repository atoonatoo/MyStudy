

----
##### 연결 문서

- 
- 
- 
---

### DB 
	데이터 베이스 - DB
    데이터베이스란, 우리가 데이터를 규격화하여 저장하는 공간으로써
    우리의 프로그램이 바뀌더라도 데이터베이스 시스템이 남아있으면 
    해당 데이터베이스 접속을 하면 기존에 입력한 데이터가 남아있게 된다. 
    데이터베이스의 기능을 가장 간략하게 설명하면 CRUD 가 된다.
    C: Create. 데이터의 생성
    R: Retrieve(Read). 데이터의 호출
    U: Update. 데이터의 수정
    D: Delete. 데이터의 삭제
    
    데이터베이스의 구조
    데이터베이스는 컬럼(튜플) -> 로우 -> 테이블 -> 스키마(=데이터베이스) 로 
    계층이 이루어져있다.
		
		
- 데이터베이스에서 작업을 하기 전에는 반드시 특정 스키마를 선택을 해주어야 한다. 
	
- 스키마를 선택할 때에는 왼쪽의 SCHEMAS 탭에서 사용할 스키마 이름을 
  더블클릭하거나 아니면 USE 스키마 이름; 을 입력해주자
	- USE sakila;
	  
- 데이터베이스에서 데이터 불러오기
	- SELECT 컬럼이름 FROM 테이블이름 
	- 어떤 데이터베이스를 쓸건지 sakila를 더블클릭해서 초점을 맞춰줘야
	  명확한 데이터가 나올 수 있음
	- SELECT actor_id FROM actor;
	  
- 만약 우리가 어떤 특정 컬럼만이 아니라 여러 컬럼을 볼때에는DI
	- SELECT 컬럼이름, 컬럼이름 FROM 테이블이름
	- SELECT actor_id, first_name FROM actor;

- 모든 컬럼을 볼떄에는
	- SELECT * FROM 테이블이름;
	- SELECT * FROM actor;
	  
- 우리가 필요에 따라서는 조건에 따른 검색이 가능하다 .
	- 이럴때에는 SELECT * FROM 테이블이름 WHERE 조건으로 검색이 가능하다.
	- 반드시 SELECT 를 사용해서 결과를 확인해야 함.
	- SELECT * FROM actor WHERE actor_id = 20;
	
- 데이터를 입력할때에는 
	- INSERT INTO 테이블이름 VALUES(값)으로 입력한다.
	- INSERT INTO actor VALUES(1080, 'Jeyung','CHO', NOW());
	- SELECT * FROM actor WHERE actor_id = 1080;
	
- 만약 우리가 특정 컬럼에만 값을 입력할 때에는 
	- INSERT INTO 테이블이름(컬럼이름1, 컬럼이름2 .....) VALUES(값1, 값2 .....); 으로 입력한다
	- INSERT INTO actor(first_name, last_name) VALUES('철수','김');
	- SELECT * FROM actor WHERE first_name = '철수';
	
- 우리가 특정 데이터의 값을 수정할 때에는 
	- UPDATE 테이블이름 SET 컬럼이름 = 새 값, 컬럼이름 = 새 값... WHERE 특정 조건
	- UPDATE actor 
	  SET first_name = '채영2', 
	  last_name = '조', 
	  last_update = NOW() 
	  WHERE actor_id = 1080;
	- SELECT * FROM actor WHERE actor_id = 1080;
	
- 로우 삭제하기
	- DELETE FROM 테이블이름 WHERE 삭제조건
	- SELECT * FROM actor WHERE actor_id = 1081;
	- DELETE FROM actor WHERE actor_id = 1081;
	- SELECT * FROM actor WHERE actor_id = 1081;
	
- 제약 조건
	- 제약 조건이란 해당 컬럼에 들어갈 값을 제약하는 특수한 조건들을 뜻한다.
	- PK: Primary Key. 해당 컬럼에 들어갈 값은 "고유" 해야하고, "null"이 아니어야한다.
	- UQ: Unique. 해당 컬럼에 들어갈 값은 "고유"해야 한다. -> 중복 값 안됨.
	- NN: Not Null. 해당 컬럼에 들어갈 값은 "널"이 아니어야 한다.
	- AI: Auto Increment. 해당 컬럼에 들어갈 정수 값은 자동으로 증가된다.
	
- 데이터타입
	- 해당 컬럼에 어떠한 값을 저장 가능한지를 지정한다.
	- 대부분 자바와 비슷하지만
	 - VARCHAR 라는 타입은 우리가 어떠한 문자열을 저장할때에 
	- 가변형 문자열이라는 특수한 타입이 된다. 
	- VARCHAR(45) 라고 한다면 , 최대 45 글자가 입력 가능하고 
	- 우리가 입력한 글자 수에 맞추어 길이가 자동으로 변경되는 타입이다.
	- 최대 길이 255
	
- PK는 왠만하면 고유키를 설정하는 것은 한개만 하는것이 관례적이다 
	
- LONGTEXT: 긴 문자열을 입력할 때.
	
- CASCADE : 탈퇴할때 모든 테이블 내에 데이터가 삭제된다.
	
- SET NULL : 탈퇴할때 모든 테이블은 그대로 있고 자신이 선택한 것만 삭제됨.
	
- 다양한 SQL 쿼리문을 알아보자
	- 1. DISTINCT
		- DISTINCT는 같은 값이 있을 경우, 하나만 보여준다.
		- USE world;
		- SELECT COUNTRYCODE FROM city;
		- SELECT DISTINCT COUNTRYCODE FROM city;
		
	- 2. AND
		- AND 는 WHERE 조건절에 복합적인 조건을 사용할때 사용한다.
		- SELECT * FROM city;
		- 컨트리코드가 AFG이고 인구가 1000000 이상인 도시
		- SELECT * FROM city WHERE countrycode = 'AFG' AND population >= 1000000;
		
	- 3. OR
		- OR은 WHERE 조건절에 '혹은' 이라는 의미로써 사용한다.
		- 컨트리코드가  AFG 혹은 인구가 1000000 이상인 도시
		- SELECT * FROM city WHERE countrycode = 'AFG' OR population >= 1000000;
		
	- 4. ORDER BY
		- ORDER BY는 특정 컬럼의 값을 토대로 정렬하여 보여준다.
		- 기본적으로 아무것도 적어주지 않으면 오름차순이지만 
		
		- ORDER BY 컬럼이름 ASC -> 해당 컬럼이름의 값으로 오름차순 정렬
		- ORDER BY 컬럼이름 DESC -> 해당 컬럼이름의 값으로 내림차순 정렬
		- SELECT * FROM city ORDER BY population ASC;
		- SELECT * FROM city ORDER BY population DESC;
		
	- 5. NOT
		- NOT은 특정 조건을 만족하지 않는 경우를 지정할때 사용이 된다.
		- SELECT * FROM city WHERE NOT countrycode = 'AFG';
		
	- 6. LIMIT
		- LIMIT은 출력되는 줄의 갯수를 제한할때 사용이 된다.
		- MySql Workbench에서는 기본적으로 출력이 LIMIT 1000이 걸려있다.
		- SELECT * FROM city LIMIT 10;
		- 또한, 특정 줄부터 총 몇개의 줄을 출력할 때에도 LIMIT이 사용된다.
		- 단, 시작되는 줄은 index와 같은 개념으로써, 0부터 시작이 된다.
		- SELECT * FROM city LIMIT 10, 20;
		
	- 7. MIN()
		- MIN()은 특정 컬럼에서 가장 작은 값을 찾아서 출력한다.
		- SELECT MIN(population) FROM city;
		
	- 8. MAX()
		- MAX()는 특정 컬럼에서 가장 큰 값을 찾아서 출력한다.
		- SELECT MAX(population) FROM city;
		
	- 9. COUNT()
		- COUNT()는 특정 컬럼의 갯수를 세어서 출력한다.
		- SELECT COUNT(name) FROM city;
		
	- 10. SUM()
		-  SUM()은 특정 컬럼의 총합을 출력한다.
		- SELECT SUM(population) FROM city;
		
	- 11. AVG()
		- AVG()는 특정 컬럼의 평균을 출력한다.
		- SELECT AVG(population) FROM city;
		
	- 12. LIKE
		- LIKE는 WHERE에서 우리가 특정 값을 적는것이 아니라 '비슷한' 값을 찾아준다.
		- %를 뒤에 붙이면 해당 글자들로 시작하는 모든 값을 찾아준다.
		- %를 앞에 붙이면 해당 글자들로 끝나는 모든 값을 찾아준다.
		- %를 앞뒤에 붙이면 해당 글자가 중간에 들어가는 모든 값을 찾아준다.
		- SELECT * FROM city
		- WHERE NAME LIKE '%se%';
		
	- 13. 어떤 특정 값들 중 하나라도 만족하는 경우를 검색할때에는 
		- IN을 쓰게 된다.
		- SELECT * FROM city
		- WHERE COUNTRYCODE IN ('KOR', 'BRA', 'JPN');
		
	- 14. 특정 범위의 값을 검색할 때에는
		- BETWEEN 시작값 AND 끝값 으로 검색하게 된다.
		- SELECT * FROM city
		- WHERE ID BETWEEN 11 AND 20;
		
	- 15. 만약 내가 검색 또는 쿼리문에서
		- 임시로 별명을 붙여주어야 하는 경우, 
		- AS 별명 으로 붙여주게 된다.
		- SELECT ID, NAME as '도시', CountryCode AS '국가' FROM city;
		
	- 16. JOIN
		- 조인은 우리가 2개의 테이블을 연결하여 결과창에서 
		  그 2개의 테이블을 모두 확인하여 원하는 결과를 뽑아볼때 사용되는 키워드이다.
		- JOIN에는 이너 조인, 레프트조인, 라이트 조인, 풀 아우터조인이 있지만
		  실질적으로 가장 많이 사용되는겐 이너 조인이 된다.
		
	- 16-1. INNER JOIN
		- city에서 countrycode를 기준으로 country 테이블을 연결하여 출력해라
		- SELECT id, C.name, countrycode, N.name 
		  FROM 
		  city AS C 
		  INNER JOIN 
		  country AS N
		  ON C.CountryCode = N.code;
		
	- 16-2. LEFT JOIN
		- city에서 id를 기준으로 country 테이블의 capital을 연결하여 출력해라
		- SELECT * FROM city
		  LEFT JOIN country
		  ON city.id = country.capital;
		
	- 16-3. RIGHT JOIN
		- SELECT * FROM city 
		  RIGHT JOIN country 
		  ON city.id = country.capital;
		
	- 17. UNION
		- 2개 이상의 SELECT 쿼리 결과를 합쳐서 보고 싶을 경우
		- SELECT * FROM CITY
		  LEFT JOIN country
		  ON city.id = country.capital
		  UNION
		  SELECT * FROM city
		  RIGHT JOIN country
		  ON city.id = country.capital;
		
	- 18. GROUP BY
		- GROUP BY란, 한 컬럼에 여러 값이 중복되어 있을 경우, 
		  한 줄로 묶음 처리 하는 것이다.
		- SELECT countrycode, sum(population) FROM city
		  GROUP BY CountryCode;
		
	- 19. Subquery
		- 서브쿼리란 IN의 조건절에 쿼리를 넣어서 해당 쿼리를 만족하는 것들만 
		  다시 뽑아내는 방법이다.
		- SELECT * FROM country WHERE code 
		  IN (SELECT countrycode FROM city);
		- SELECT * FROM country
		  WHERE capital IN (SELECT id from city);
		- SELECT * FROM city
		  INNER JOIN country ON city.id = country.capital
		  WHERE city.population >= 5000000
		  ORDER BY city.name DESC;
		
		
		

### DB 예제 1

	USE sakila;
	- 배우 : actor | 영화 : film | 고객 : customer | 영화_배우 : film_actor
	- store : inventory
	1. 배우의 이름을 알파벳 내림차순 10명을 보여주세요.
		SELECT first_name FROM actor ORDER BY first_name DESC LIMIT 10;
		
	2. 영화의 카테고리를 보여주세요.
		SELECT * FROM film_category;
		
	3. 고객 중에 휴면 회원들을 모두 보여주세요.
		SELECT * FROM customer WHERE active = 0;
		
	4. 영화를 대여기간 순으로 오름차순 정렬하세요
		SELECT * FROM film ORDER BY rental_duration ASC;
		
	5. 영화를 대여료 순으로 내림차순 정렬하세요.
		SELECT film.rental_rate FROM film ORDER BY rental_rate DESC;
		
	6. 영화 중 개(dog)가 나오는 것을 모두 보여주세요.
		SELECT * from film WHERE description like '%dog%';
		
	7. 영화 중 2010년 이전에 나온 영화들을 모두 보여주세요.
		SELECT title, release_year FROM film WHERE release_year <= 2010;
		
	8. 필름 액터 테이블로 페넬로페 귀네스가 나온 영화의 제목들을 출력해주세요.
		SELECT * from actor 
		where first_name = 'penelope' 
		and last_name = 'guiness';
		
		select * from film_actor inner join actor
		on film_actor_id = actor.actor_id
		where actor.first_name = 'penelope' and last_name = 'guiness';
		
		select film.title from film
		inner join film_actor
		on film.film_id = film_actor.film_id
		inner join actor
		on film_actor.actor_id = actor.actor_id
		where actor.first_name = 'penelope' and actor.last_name = 'guiness';
		
	9. 가장 많은 영화에 출연한 배우의 성과 이름과 출연한 영화의 갯수를 출력해주세요.
		SELECT  actor.first_name, actor.last_name, count(fa.actor_id) 
		FROM film_actor as fa
		inner join actor 
		on fa.actor_id = actor.actor_id
		GROUP BY fa.actor_id
		order by count(fa.actor_id) desc
		limit 1; #첫번째 배우가 제일 많이 출연한 배우이기 때문에 
		
	10. 회원 번호와 그 회원이 대여료를 총 얼마 냈는지 보여주세요.
		select customer_id, sum(amount) from payment
		group by customer_id;
	
	11. 1번 store가 가지고 있는 총 비디오의 갯수를 보여주세요.
		select count(*) from inventory where store_id=1;
	
	12. 1번 store가 가지고 있는 영화와 해당 영화의 비디오 갯수를 보여주세요.
		select film.title, count(inventory.inventory_id) 
		from film
		inner join inventory 
		on film.film_id = inventory.film_id
		where store_id = 1
		group by inventory.film_id;
	
	13. 영화의 제목과 카테고리를 텍스트로 보여주세요.
		select title, name from film_category
		inner join category
		on film.category.category_id= category.category_id
		inner join film
		on film_category.film_id = film.film_id;
	
	14. 도시와 해당 국가를 보여주세요.
		select city, country from city
		inner join country
		on city.country_id = country.country_id;
	
	15. 고객 중 미국에 살고 있는 회원의 이름과 이메일을 보여주세요.
		select * from customer;
		select * from address;
		select * from city;
		select * from country;
		
		select * from address
		where city_id in 
		(select city_id from city where country_id = (
		select country_id from country where country = "United States"));
		
		select first_name, last_name, email from customer
		where address_id 
		in (select address_id from address
		   where city_id in
		      (select city_id from city 
		         where country_id =
		            (select country_id from country 
		            where country = "United States")));
	
	16. 영화 중 대여횟수가 가장 많은 영화의 이름을 보여주세요.
		select * from rental;
		select * from inventory;
		
		select title, count(inventory.film_id)
		from rental
		inner join inventory
		on rental.inventory_id = inventory.inventory_id
		inner join film
		on film.film_id = inventory.film_id
		group by inventory.film_id
		order by count(film_id) desc
		limit 1;
	
	17. 영화 중 대여기간이 4일 미만이고 주연의 이름이 JOHNNY LOLLOBRIGIDA 이고 
	    비디오 부록에 예고편이 있는 영화의 제목을 보여주세요.
		select * from film
		where film.special_features like '%Trailers%'
		and rental_duration < 4;
		
		select * from actor
		where first_name = 'JOHNNY' and last_name = 'LOLLOBRIGIDA';
		
		select * from actor
		inner join film_actor
		on actor.actor_id = film_actor.actor_id
		where first_name = 'JOHNNY' and last_name = 'LOLLOBRIGIDA';
		
		select * from film
		inner join film_actor
		on film.film_id = film_actor.film_id
		where actor.first_name = 'JOHNNY'
		and last_name = 'LOLLOBRIGIDA'
		and film.special_features like '%Trailers%'
		and film.rental_duration < 4;
	
	18. 직원 중 Mike Hillyer가 LINDA WILLAMS 에게 대여해준 
	    영화의 제목, 대여일, 반납일을 보여주세요.
		select* from staff;
		select * from rental;
		select * from inventory;
		select * from film;
		
		select* from staff
		where first_name = 'Mike' and last_name = 'Hillyer';
		
		select* from customer
		where first_name = 'Linda' and last_name = 'Williams';
		
		select film.title, rental.rental_date, rental.return_date from rental
		inner join staff
		on rental.staff_id = staff.staff_id
		inner join customer
		on rental.customer_id = customer.customer_id
		inner join inventory
		on rental.inventory_id = inventory.inventory_id
		inner join film
		on inventory.film_id = film.film_id
		where staff.first_name = 'Mike' and staff.last_name = 'Hillyer'
		and customer.first_name = 'Linda' and customer.last_name = 'Williams';
	
	19. 영화의 이름과 출연한 배우의 숫자를 배우의 숫자로 내림차순해서 보여주되 
	    출연한배우의 숫자 컬럼의 이름을 출연배우수로 만들어 보여세요.
		select * from film_actor;
		
		select title, count(*) as '출연배우수'
		from film_actor
		inner join film
		on film_actor.film_id = film.film_id
		group by film_actor.film_id
		order by 출연배우수 desc;
		
	20. 회원의 이름, 빌린 비디오의 숫자, 빌린 비디오 대여점의 주소, 
	    회원의 거주 도시를 회원 번호순으로 정렬하여 보여주세요.
		SELECT * FROM customer;
		SELECT COUNT(*) FROM rental
		GROUP BY inventory_id;
		SELECT * FROM STORE;
		SELECT * FROM address;
		SELECT * FROM city;
		
		SELECT customer.first_name, customer.last_name, 
		city.city, customer_city.city FROM rental
		INNER JOIN customer
		ON rental.customer_id = customer.customer_id
		INNER JOIN STAFF
		ON rental.staff_id = staff.staff_id
		INNER JOIN STORE
		ON staff.store_id = store.store_id
		INNER JOIN ADDRESS
		ON store.address_id = address.address_id
		INNER JOIN CITY
		ON address.city_id = city.city_id
		INNER JOIN ADDRESS AS customer_address
		ON customer.address_id = customer_address.address_id
		INNER JOIN CITY AS customer_city
		ON customer_address.city_id = customer_city.city_id;

- 데이터베이스 계정 비밀번호 변경
	- alter user 'root'@'localhost' identified with mysql_native_password by 'new password';

- MYSQL 덤프 파일 추출하는 방법
	- cmd 접속 (관리자 권한으로)
	- 입력
		- cd 경로로 이동
			- cd "C:\Program Files\MySQL\MySQL Server 8.1\bin"
		- mysqldump -u 'username' -p'password' 'database' > '파일명'.sql
			- mysqldump -u root -p1234 coupang > dump.sql
	- 경로에서 파일이 생성된다.
		- C:\Program Files\MySQL\MySQL Server 8.1
	- 덤프 파일 임포트
		- mysql -u root -p1234 nc_board < "C:\Program Files\MySQL\MySQL Server 8.1"