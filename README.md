# PSQLOdev1
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
SELECT * FROM film
ORDER BY title , description;

2.film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
SELECT * FROM film
ORDER BY length > 60 AND length < 75;

3.film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
SELECT * FROM film
ORDER BY rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99;

4.customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
Smith

5.film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
SELECT * FROM film
WHERE NOT length > 50 AND rental_rate = 2.99 OR rental_rate = 4.99; 

# PSQLOdev2
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
SELECT * FROM film
WHERE replacement_cost BETWEEN  12.99 AND  16.99;

2.actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penolope','Nick','Ed');

3.film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
SELECT * FROM film
WHERE rental_rate IN (0.99,2.99,4.99) AND replacement_cost IN (12.99,15.99,28.99);

# PSQLOdev3
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
SELECT country FROM country
WHERE country  LIKE 'A&a';

2.country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
SELECT country FROM country
WHERE country LIKE '%N' 

3.film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
SELECT title FROM film
WHERE title ILIKE 'T%'

4.film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
SELECT * FROM film
WHERE title LIKE 'C' AND length > 90 AND rental_rate = 2.99

# PSQLOdev4
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
SELECT DISTINCT replacement_cost FROM film;

2.film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
SELECT COUNT (DISTINCT replacement_cost) FROM film;

3.film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
SELECT COUNT (*) FROM film
WHERE title LIKE 'T%' AND rating IN ('G');

4.country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
SELECT COUNT (*) FROM country
WHERE country LIKE '_____';

5.city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
SELECT COUNT (*) FROM city
WHERE city ILIKE '%r';

# PSQLOdev5
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

SELECT * FROM film
WHERE title ILIKE '%n'
ORDER BY length DESC 
LIMIT 5;

2.film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

SELECT * FROM film
WHERE title ILIKE '%n'
ORDER BY length ASC
LIMIT 5;

3.customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

SELECT last_name FROM customer
WHERE store_id = 1
LIMIT 4;

# PSQLOdev6
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

SELECT AVG (rental_rate) FROM film;

2.film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

SELECT COUNT (*) FROM film
WHERE title LIKE 'C&';

3.film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

SELECT MAX (length) FROM film
WHERE rental_rate = 0.99;

4.film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

SELECT COUNT (DISTINCT replacement_cost) FROM film
WHERE length > 150;

# PSQLOdev7
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

SELECT rating FROM film
GROUP BY rating;

2.film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

SELECT replacement_cost, COUNT (*) FROM film 
GROUP BY replacement_cost 
HAVING COUNT (*) > 50
ORDER BY replacement_cost;

3.customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

SELECT COUNT (store_id) FROM customer
GROUP BY store_id;


4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

SELECT country_id FROM city
GROUP BY country_id;

SELECT MAX (country_id) FROM country;

SELECT MAX (country), COUNT (*) FROM country;

# PSQLOdev8
SQL ödevi

1.test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

CREATE TABLE employee (
	id INTEGER,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(100)
)

2.Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

insert into employee (id, name, birthday, email) values (1, 'Alix', '2022-07-30', 'ainsull0@youtube.com');
insert into employee (id, name, birthday, email) values (2, 'Fidelity', '2022-05-17', 'fcushworth1@dailymotion.com');
insert into employee (id, name, birthday, email) values (3, 'Hannie', '2023-01-07', 'hvass2@artisteer.com');
insert into employee (id, name, birthday, email) values (4, 'Robinette', '2022-10-26', 'rmedcalf3@admin.ch');
insert into employee (id, name, birthday, email) values (5, 'Samaria', '2022-10-16', 'sbratty4@g.co');
insert into employee (id, name, birthday, email) values (6, 'Grace', '2022-10-06', 'gdethloff5@sina.com.cn');
insert into employee (id, name, birthday, email) values (7, 'Marcy', '2022-04-03', 'melkington6@guardian.co.uk');
insert into employee (id, name, birthday, email) values (8, 'Vernor', '2022-03-03', 'vmacgilrewy7@last.fm');
insert into employee (id, name, birthday, email) values (9, 'Emmye', '2022-12-07', 'eambrogio8@topsy.com');
insert into employee (id, name, birthday, email) values (10, 'Karyn', '2022-03-27', 'kcocker9@opensource.org');
insert into employee (id, name, birthday, email) values (11, 'Gunther', '2022-11-22', 'gshovelina@discuz.net');
insert into employee (id, name, birthday, email) values (12, 'Ben', '2022-02-23', 'bdykab@aol.com');
insert into employee (id, name, birthday, email) values (13, 'Colas', '2022-04-21', 'ccarissc@sohu.com');
insert into employee (id, name, birthday, email) values (14, 'Kerrie', '2022-12-16', 'kdanyd@livejournal.com');
insert into employee (id, name, birthday, email) values (15, 'Brnaby', '2022-10-20', 'bvernazzae@npr.org');
insert into employee (id, name, birthday, email) values (16, 'Egan', '2022-07-08', 'ecolwellf@woothemes.com');
insert into employee (id, name, birthday, email) values (17, 'Karie', '2022-05-04', 'kutridgeg@ed.gov');
insert into employee (id, name, birthday, email) values (18, 'Lorinda', '2022-10-13', 'lbrinsonh@liveinternet.ru');
insert into employee (id, name, birthday, email) values (19, 'Nina', '2022-05-13', 'nbatmani@baidu.com');
insert into employee (id, name, birthday, email) values (20, 'Klara', '2022-01-30', 'kklessej@usatoday.com');
insert into employee (id, name, birthday, email) values (21, 'Ephraim', '2022-08-13', 'emethingamk@techcrunch.com');
insert into employee (id, name, birthday, email) values (22, 'Guthry', '2022-11-20', 'gharrimanl@seesaa.net');
insert into employee (id, name, birthday, email) values (23, 'Cordell', '2022-12-20', 'cpalingm@businessinsider.com');
insert into employee (id, name, birthday, email) values (24, 'Phil', '2023-01-06', 'pcastellaccion@cdbaby.com');
insert into employee (id, name, birthday, email) values (25, 'Barry', '2022-11-14', 'broschero@barnesandnoble.com');
insert into employee (id, name, birthday, email) values (26, 'Christie', '2022-02-01', 'cbignalp@shop-pro.jp');
insert into employee (id, name, birthday, email) values (27, 'Shari', '2022-05-09', 'sklichq@woothemes.com');
insert into employee (id, name, birthday, email) values (28, 'Janeva', '2022-05-31', 'jperksr@blogs.com');
insert into employee (id, name, birthday, email) values (29, 'Shell', '2022-12-24', 'sdenges@soup.io');
insert into employee (id, name, birthday, email) values (30, 'Sibelle', '2022-02-10', 'sbloxsomt@narod.ru');
insert into employee (id, name, birthday, email) values (31, 'Baldwin', '2022-01-27', 'bbeldanu@skype.com');
insert into employee (id, name, birthday, email) values (32, 'Hayward', '2022-02-08', 'hnovicv@about.com');
insert into employee (id, name, birthday, email) values (33, 'Jemima', '2022-09-24', 'jteaserw@icq.com');
insert into employee (id, name, birthday, email) values (34, 'Laureen', '2022-04-21', 'lroloffx@paginegialle.it');
insert into employee (id, name, birthday, email) values (35, 'Allen', '2022-12-27', 'adomey@wsj.com');
insert into employee (id, name, birthday, email) values (36, 'Eustace', '2022-12-12', 'enickersonz@bing.com');
insert into employee (id, name, birthday, email) values (37, 'Joanne', '2022-07-29', 'jstitle10@lycos.com');
insert into employee (id, name, birthday, email) values (38, 'Dasie', '2022-11-07', 'dlaunder11@washingtonpost.com');
insert into employee (id, name, birthday, email) values (39, 'Coral', '2022-03-16', 'cbrecknell12@wikispaces.com');
insert into employee (id, name, birthday, email) values (40, 'Nathan', '2022-04-16', 'nmehaffey13@bbc.co.uk');
insert into employee (id, name, birthday, email) values (41, 'Chase', '2022-10-03', 'cfrancino14@goo.ne.jp');
insert into employee (id, name, birthday, email) values (42, 'Darby', '2022-03-06', 'dwaddams15@cdbaby.com');
insert into employee (id, name, birthday, email) values (43, 'Son', '2022-11-01', 'smcpherson16@deviantart.com');
insert into employee (id, name, birthday, email) values (44, 'Joycelin', '2022-03-04', 'jpulman17@delicious.com');
insert into employee (id, name, birthday, email) values (45, 'Craggy', '2022-07-17', 'cdrissell18@weibo.com');
insert into employee (id, name, birthday, email) values (46, 'Delphinia', '2022-09-24', 'dgoodhand19@ted.com');
insert into employee (id, name, birthday, email) values (47, 'Griswold', '2022-02-12', 'gpicardo1a@google.cn');
insert into employee (id, name, birthday, email) values (48, 'Eb', '2022-11-16', 'ekerford1b@blog.com');
insert into employee (id, name, birthday, email) values (49, 'Justin', '2022-07-19', 'jheak1c@discuz.net');
insert into employee (id, name, birthday, email) values (50, 'Jillane', '2022-02-24', 'jgeck1d@ted.com');
insert into employee (id, name, birthday, email) values (51, 'Jewell', '2022-06-24', 'jtobias1e@bbc.co.uk');
insert into employee (id, name, birthday, email) values (52, 'Arni', '2022-08-28', 'ablazdell1f@hud.gov');
insert into employee (id, name, birthday, email) values (53, 'Sheffield', '2022-12-16', 'solennachain1g@google.co.uk');
insert into employee (id, name, birthday, email) values (54, 'Scarlett', '2022-10-11', 'sbosward1h@utexas.edu');
insert into employee (id, name, birthday, email) values (55, 'Keary', '2022-08-18', 'kburkill1i@tiny.cc');
insert into employee (id, name, birthday, email) values (56, 'Jordon', '2022-02-26', 'jgosz1j@ow.ly');
insert into employee (id, name, birthday, email) values (57, 'Estrella', '2022-01-14', 'eshowalter1k@weibo.com');
insert into employee (id, name, birthday, email) values (58, 'Dom', '2022-02-20', 'dellacombe1l@artisteer.com');
insert into employee (id, name, birthday, email) values (59, 'Corny', '2022-06-30', 'crubinlicht1m@google.pl');
insert into employee (id, name, birthday, email) values (60, 'Zacherie', '2022-10-22', 'zcankett1n@vk.com');
insert into employee (id, name, birthday, email) values (61, 'Hewett', '2022-11-28', 'hlundberg1o@discuz.net');
insert into employee (id, name, birthday, email) values (62, 'Al', '2022-12-11', 'arosenwasser1p@nsw.gov.au');
insert into employee (id, name, birthday, email) values (63, 'Jess', '2022-06-15', 'jmitrikhin1q@clickbank.net');
insert into employee (id, name, birthday, email) values (64, 'Regan', '2022-02-22', 'rorts1r@weibo.com');
insert into employee (id, name, birthday, email) values (65, 'Leela', '2022-12-09', 'lmcaw1s@seesaa.net');
insert into employee (id, name, birthday, email) values (66, 'Marisa', '2022-05-30', 'mlethibridge1t@godaddy.com');
insert into employee (id, name, birthday, email) values (67, 'Juliann', '2022-03-01', 'jweetch1u@un.org');
insert into employee (id, name, birthday, email) values (68, 'Natala', '2022-11-19', 'nrawling1v@taobao.com');
insert into employee (id, name, birthday, email) values (69, 'Goldy', '2022-07-24', 'grapsey1w@sina.com.cn');
insert into employee (id, name, birthday, email) values (70, 'Hercules', '2022-11-22', 'hoffin1x@theguardian.com');
insert into employee (id, name, birthday, email) values (71, 'Lezlie', '2022-10-14', 'lriccelli1y@plala.or.jp');
insert into employee (id, name, birthday, email) values (72, 'Marilin', '2022-09-20', 'mcraggs1z@taobao.com');
insert into employee (id, name, birthday, email) values (73, 'Maxy', '2022-05-30', 'mthackwray20@google.fr');
insert into employee (id, name, birthday, email) values (74, 'Maisey', '2022-01-17', 'mplaice21@amazon.co.uk');
insert into employee (id, name, birthday, email) values (75, 'Editha', '2022-11-24', 'eguenther22@xinhuanet.com');
insert into employee (id, name, birthday, email) values (76, 'Addison', '2022-04-14', 'adawtry23@intel.com');
insert into employee (id, name, birthday, email) values (77, 'Francklin', '2022-06-03', 'fnevin24@mlb.com');
insert into employee (id, name, birthday, email) values (78, 'Benita', '2022-10-08', 'bpratt25@slate.com');
insert into employee (id, name, birthday, email) values (79, 'Jaquelyn', '2022-07-21', 'jmcorkill26@examiner.com');
insert into employee (id, name, birthday, email) values (80, 'Deidre', '2022-10-08', 'dburberye27@virginia.edu');
insert into employee (id, name, birthday, email) values (81, 'Andra', '2022-02-07', 'acondie28@devhub.com');
insert into employee (id, name, birthday, email) values (82, 'Willis', '2022-01-30', 'wfieller29@usgs.gov');
insert into employee (id, name, birthday, email) values (83, 'Brigitta', '2022-08-04', 'bhowes2a@ed.gov');
insert into employee (id, name, birthday, email) values (84, 'Louise', '2022-02-05', 'lpavlenkov2b@ebay.com');
insert into employee (id, name, birthday, email) values (85, 'Vera', '2022-09-30', 'vasple2c@ibm.com');
insert into employee (id, name, birthday, email) values (86, 'Faustine', '2022-03-16', 'fheinsh2d@mapy.cz');
insert into employee (id, name, birthday, email) values (87, 'Roma', '2022-10-07', 'rcolafate2e@canalblog.com');
insert into employee (id, name, birthday, email) values (88, 'Cheri', '2022-02-14', 'candrioli2f@dagondesign.com');
insert into employee (id, name, birthday, email) values (89, 'Ivar', '2022-01-29', 'icleyne2g@walmart.com');
insert into employee (id, name, birthday, email) values (90, 'Salli', '2022-02-23', 'sjozsika2h@prnewswire.com');
insert into employee (id, name, birthday, email) values (91, 'Yulma', '2022-12-27', 'ysommersett2i@un.org');
insert into employee (id, name, birthday, email) values (92, 'Jeramie', '2022-05-15', 'jchalfant2j@taobao.com');
insert into employee (id, name, birthday, email) values (93, 'Giorgi', '2022-01-21', 'gceliz2k@bandcamp.com');
insert into employee (id, name, birthday, email) values (94, 'Giralda', '2022-07-02', 'gbedow2l@desdev.cn');
insert into employee (id, name, birthday, email) values (95, 'Nona', '2022-08-01', 'ndunkerly2m@skyrock.com');
insert into employee (id, name, birthday, email) values (96, 'Axe', '2022-06-09', 'ajolliff2n@sfgate.com');
insert into employee (id, name, birthday, email) values (97, 'Lynnea', '2022-12-15', 'lwhilder2o@51.la');
insert into employee (id, name, birthday, email) values (98, 'Mikkel', '2022-03-08', 'mlark2p@t.co');
insert into employee (id, name, birthday, email) values (99, 'Maure', '2022-12-17', 'mdungate2q@macromedia.com');
insert into employee (id, name, birthday, email) values (100, 'Layla', '2022-08-04', 'lthripp2r@spiegel.de');

3.Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

UPDATE employee 
SET name = 'Şermin Yaşar',
	birthday = '1990-12-06',
	email = 'sermin@yasar.com'
	WHERE id = 4;
	
UPDATE employee 
SET name = 'Hakan Yılmaz',
	birthday = '1995-12-06',
	email = 'hakan@yılmaz.com'
	WHERE id = 71;
	
UPDATE employee 
SET name = 'Leyla Doğramacı',
	birthday = '1980-11-01',
	email = 'leyladogra@gmail.com'
	WHERE id = 99;
	
UPDATE employee 
SET name = 'Zambak Çiçek',
	birthday = '2001-12-06',
	email = 'zambak@ciceek.com'
	WHERE id = 88;
	
UPDATE employee 
SET name = 'Anne Shirley',
	birthday = '1970-06-06',
	email = 'Annewithe@gmail.com'
	WHERE id = 10;

4.Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
  DELETE FROM employee
WHERE id = 65;	

DELETE FROM employee 
WHERE id > 50;

DELETE FROM employee
WHERE id = 48;

DELETE FROM employee
WHERE id = 15;

DELETE FROM employee 
WHERE id = 12;

# PSQLOdev9
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

SELECT city, country FROM city
INNER JOIN country ON city.city_id = country.country_id;

2.customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

SELECT payment.payment_id, customer.first_name, customer.last_name FROM payment
INNER JOIN customer ON payment.customer_id = customer.customer_id;

3.customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

SELECT rental.rental_id, customer.first_name, customer.last_name FROM rental
INNER JOIN customer ON rental.rental_id = customer.customer_id;

# PSQLOdev10
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

SELECT city, country FROM country
LEFT JOIN city ON city.city_id = country.country_id;

2.customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

SELECT customer.first_name, customer.last_name , payment.payment_id FROM customer
RIGHT JOIN payment ON payment.payment_id = customer.customer_id;

3.ustomer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

SELECT customer.first_name, customer.last_name , rental.rental_id FROM customer
FULL JOIN rental ON rental.rental_id = customer.customer_id;

# PSQLOdev11
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);

2.actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

(SELECT first_name FROM actor)
INTERSECT 
(SELECT first_name FROM customer);

3.actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM customer);

4.İlk 3 sorguyu tekrar eden veriler için de yapalım.

1. (SELECT first_name FROM actor
LIMIT 10)
INTERSECT
(SELECT first_name FROM customer
LIMIT 10);

2. (SELECT first_name FROM actor 
LIMIT 20)
INTERSECT 
(SELECT first_name FROM customer
LIMIT 20);

3. (SELECT first_name FROM actor
LIMIT 50)
INTERSECT
(SELECT first_name FROM customer
LIMIT 50);

# SQLOdev12
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

SELECT COUNT (length) FROM film
WHERE length > (SELECT AVG(length) FROM film);

2.film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

SELECT COUNT (rental_rate) FROM film
WHERE rental_rate = (SELECT MAX (rental_rate) FROM film);

3.film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

SELECT COUNT (*) FROM film
WHERE (rental_rate, replacement_cost) = (SELECT MIN (rental_rate), MIN (replacement_cost) FROM film);

4.payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

SELECT COUNT (customer_id) FROM payment
WHERE amount = (SELECT MAX (amount) FROM payment);
