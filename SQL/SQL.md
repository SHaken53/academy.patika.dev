# SQL Eğitimi

> Bu repo'da Patika.dev'in [SQL](https://academy.patika.dev/courses/sql) eğitiminde verilen ödevlerin cevapları bulunmaktadır.

# SQL Ödev 01 | 

1. film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

` 
SELECT title, description FROM film; 
`

2. film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

` 
SELECT * FROM film WHERE length > 60 AND length < 75;
`

3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

` 
SELECT * FROM film WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
`

4. customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

` 
SELECT last_name FROM customer WHERE first_name = 'Mary';
`

5. film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

` 
SELECT * FROM film WHERE length <= 50 AND rental_rate NOT IN (2.99, 4.99);
`

# SQL Ödev 02 | 


1. film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

`
SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99;
`

2. .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

`
SELECT first_name, last_name FROM actor WHERE first_name IN ('Penelope', 'Nick', 'Ed');
`

3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

`
SELECT * FROM film WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
`

# SQL Ödev 03 |

1. country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

`
SELECT * FROM country WHERE country LIKE 'A%a';
`

2. country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

`
SELECT * FROM country WHERE LENGTH(country) >= 6 AND country LIKE '%n';
`

3. film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

`
SELECT * FROM film WHERE title LIKE '%T%T%T%T%';
`

4. film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

`
SELECT * FROM film WHERE title LIKE 'C%' AND LENGTH(title) > 90 AND rental_rate = 2.99;
`

# SQL Ödev 04 |

1. film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

`
SELECT DISTINCT replacement_cost FROM film;
`

2. film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

`
SELECT COUNT(DISTINCT replacement_cost) FROM film;
`

3. film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

`
SELECT COUNT(*) FROM film WHERE title LIKE 'T%' AND rating = 'G';
`

4. country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

`
SELECT COUNT(*) FROM country WHERE LENGTH(country) = 5;
`

5. city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

`
SELECT COUNT(*) FROM city WHERE city LIKE '%r' OR city LIKE '%R';
`

# SQL Ödev 05 |

1. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

`
SELECT *
FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
`

2. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

`
SELECT *
FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
LIMIT 5
OFFSET 1;
`

3. customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

`
SELECT *
FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
`

# SQL Ödev 06 |

1. film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

`
SELECT AVG(rental_rate) AS average_rental_rate
FROM film;
`

2. film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

`
SELECT COUNT(*)
FROM film
WHERE title LIKE 'C%';
`

3. film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

`
SELECT MAX(length) AS max_length
FROM film
WHERE rental_rate = 0.99;
`

4. film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

`
SELECT COUNT(DISTINCT replacement_cost)
FROM film
WHERE length > 150;
`

# SQL Ödev 07 |

1. film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

`
SELECT rating, COUNT(*) AS film_count
FROM film
GROUP BY rating;
`

2. film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

`
SELECT replacement_cost, COUNT(*) AS film_count
FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
`

3. customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

`
SELECT store_id, COUNT(*) AS customer_count
FROM customer
GROUP BY store_id;
`

4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

`
SELECT country_id, COUNT(*) AS city_count
FROM city
GROUP BY country_id
ORDER BY city_count DESC
LIMIT 1;
`

# SQL Ödev 08 |

1. test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

`
CREATE TABLE employee (
  id INTEGER,
  name VARCHAR(50),
  birthday DATE,
  email VARCHAR(100)
);
`

2. Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

`
INSERT INTO employee (id, name, email, birthday) VALUES
(1, 'Ahmet', 'ahmet@example.com', '1990-01-01'),
(2, 'Ayşe', 'ayse@example.com', '1991-02-05'),
(3, 'Mehmet', 'mehmet@example.com', '1985-03-10'),
(4, 'Fatma', 'fatma@example.com', '1988-04-15'),
(5, 'Ali', 'ali@example.com', '1992-05-20'),
(6, 'Zeynep', 'zeynep@example.com', '1987-06-25'),
(7, 'Mustafa', 'mustafa@example.com', '1993-07-30'),
(8, 'Elif', 'elif@example.com', '1989-08-04'),
(9, 'Emre', 'emre@example.com', '1994-09-09'),
(10, 'Ayhan', 'ayhan@example.com', '1995-10-14'),
(11, 'Hülya', 'hulya@example.com', '1990-11-19'),
(12, 'Murat', 'murat@example.com', '1986-12-24'),
(13, 'Selin', 'selin@example.com', '1991-01-02'),
(14, 'Can', 'can@example.com', '1985-02-07'),
(15, 'Sevgi', 'sevgi@example.com', '1988-03-12'),
(16, 'Hakan', 'hakan@example.com', '1992-04-17'),
(17, 'İrem', 'irem@example.com', '1987-05-22'),
(18, 'Deniz', 'deniz@example.com', '1993-06-27'),
(19, 'Gül', 'gul@example.com', '1989-07-01'),
(20, 'Onur', 'onur@example.com', '1994-08-06'),
(21, 'Gizem', 'gizem@example.com', '1995-09-11'),
(22, 'Tolga', 'tolga@example.com', '1990-10-16'),
(23, 'Aslı', 'asli@example.com', '1986-11-21'),
(24, 'Eren', 'eren@example.com', '1991-12-26'),
(25, 'Aylin', 'aylin@example.com', '1992-01-03'),
(26, 'Yasin', 'yasin@example.com', '1988-02-08'),
(27, 'Melis', 'melis@example.com', '1993-03-13'),
(28, 'Özgür', 'ozgur@example.com', '1989-04-18'),
(29, 'Ebru', 'ebru@example.com', '1994-05-23'),
(30, 'Serkan', 'serkan@example.com', '1985-06-28'),
(31, 'Büşra', 'busra@example.com', '1990-07-03'),
(32, 'Mert', 'mert@example.com', '1995-08-08'),
(33, 'Ceyda', 'ceyda@example.com', '1986-09-12'),
(34, 'Berkan', 'berkan@example.com', '1991-10-17'),
(35, 'Seda', 'seda@example.com', '1992-11-22'),
(36, 'Uğur', 'ugur@example.com', '1988-12-27'),
(37, 'Esra', 'esra@example.com', '1993-01-04'),
(38, 'Kerem', 'kerem@example.com', '1989-02-09'),
(39, 'Derya', 'derya@example.com', '1994-03-14'),
(40, 'Aliye', 'aliye@example.com', '1985-04-19'),
(41, 'Ercan', 'ercan@example.com', '1990-05-24'),
(42, 'Gözde', 'gozde@example.com', '1995-06-29'),
(43, 'Cihan', 'cihan@example.com', '1986-08-04'),
(44, 'Buse', 'buse@example.com', '1991-09-09'),
(45, 'Arda', 'arda@example.com', '1992-10-14'),
(46, 'Pelin', 'pelin@example.com', '1988-11-19'),
(47, 'Kadir', 'kadir@example.com', '1993-12-24'),
(48, 'Ayça', 'ayca@example.com', '1989-01-02'),
(49, 'Efe', 'efe@example.com', '1994-02-07'),
(50, 'Yasemin', 'yasemin@example.com', '1985-03-13');
`

3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

`
UPDATE employee
SET name = 'Sabri',
email = 'sabri@sbr.com',
birthday = '2000-12-20'
WHERE id = '20';
`

`
UPDATE employee
SET name = 'Hakan',
email = 'hakan@hkn.com',
birthday = '2005-09-02'
WHERE name = 'Eren';
`

`
UPDATE employee
SET name = 'Kerem',
email = 'kerem@krm.com',
birthday = '2003-09-02'
WHERE birthday-- = '1985-03-13';
`

`
UPDATE employee
SET name = 'Berkan',
email = 'berkan@brkn.com',
birthday = '1998-03-20'
WHERE email = 'ayca@example.com';
`

`
UPDATE employee
SET name = 'XX',
email = 'yy@zz.com',
birthday = '2002-02-02'
WHERE name ILIKE 'D%' AND name ILIKE '%O';
`

4. Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

`
DELETE FROM employee
WHERE id = 2;
`

`
DELETE FROM employee
WHERE name = 'Uğur';
`

`
DELETE FROM employee
WHERE email = 'mert@example.com';
`

`
DELETE FROM employee
WHERE birthday = '1994-05-23';
`

`
DELETE FROM employee
WHERE name ILIKE 'K%' AND name ILIKE '%r';
`

# SQL Ödev 09 |

1. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

`
SELECT city.city, country.country
FROM city
INNER JOIN country ON city.country_id = country.country_id;
`

2. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

`
SELECT customer.first_name, customer.last_name, payment.payment_id
FROM customer
INNER JOIN payment ON customer.customer_id = payment.customer_id;
`

3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

`
SELECT customer.first_name, customer.last_name, rental.rental_id
FROM customer
INNER JOIN rental ON customer.customer_id = rental.customer_id;
`

# SQL Ödev 10 |

1. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

`
SELECT city.city, country.country
FROM city
LEFT JOIN country ON city.country_id = country.country_id;
`

2. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

`
SELECT customer.first_name, customer.last_name, payment.payment_id
FROM customer
RIGHT JOIN payment ON customer.customer_id = payment.customer_id;
`

3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

`
SELECT customer.first_name, customer.last_name, rental.rental_id
FROM customer
FULL JOIN rental ON customer.customer_id = rental.customer_id;
`

# SQL Ödev 11 |

1. actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

`
SELECT first_name FROM actor
UNION
SELECT first_name FROM customer;
`

2. actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

`
SELECT first_name FROM actor
INTERSECT
SELECT first_name FROM customer;
`

3. actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

`
SELECT first_name FROM actor
EXCEPT
SELECT first_name FROM customer;
`

4. İlk 3 sorguyu tekrar eden veriler için de yapalım.

-- Tüm verileri sıralama
`
SELECT first_name FROM actor
UNION ALL
SELECT first_name FROM customer;
`

-- Kesişen verileri sıralama
`
SELECT first_name FROM actor
INNER JOIN customer ON actor.first_name = customer.first_name;
`

-- İlk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralama
`
SELECT first_name FROM actor
WHERE first_name NOT IN (SELECT first_name FROM customer);
`

# SQL Ödev 12 |

1. film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

`
SELECT COUNT(*) FROM film WHERE length > (SELECT AVG(length) FROM film);
`

2. film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

`
SELECT COUNT(*) FROM film WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);
`

3. film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

`
SELECT * FROM film WHERE rental_rate = (SELECT MIN(rental_rate) FROM film) AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);
`

4. payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

`
SELECT customer_id, COUNT(*) as total_payments FROM payment GROUP BY customer_id ORDER BY total_payments DESC LIMIT 5;
`
