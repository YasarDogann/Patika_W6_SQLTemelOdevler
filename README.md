# Patika+ Week6 SQL ile Temel Ödev Uygulaması
Merhaba,
Bu proje SQL ile Patika+ 6.hafta SQL komutları pratik için yapılmış bir uygulamadır.

## 📚 Proje Hakkında
Bu proje, aşağıdaki konuları öğrenmeye yardımcı olmak için tasarlanmıştır:
- Temel SQL komutları
- WHERE kullanımı
- AND ve OR kullanımı
- BETWEEN kullanımı
- IN kullanımı
- LIKE ve ILIKE
- DISTINCT ve COUNT kullanımı


## ÖDEV 1 KOD:
```sql

/*Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

 1. film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
 2. film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
 3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
 4. customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
 5. film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
	*/

-- 1.SORU
SELECT title, description FROM film;

-- 2.SORU
SELECT * FROM film
WHERE length > 60 AND length < 75;

-- 3.SORU
SELECT * FROM film
WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);

-- 4.SORU
SELECT first_name, last_name FROM customer
WHERE first_name = 'Mary';	

-- 5.SORU
SELECT * FROM film
WHERE length < 50 AND NOT(rental_rate = 2.99 OR rental_rate = 4.99);

```

## ÖDEV 2 KOD:
```sql
/*
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
  1. film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla 
  sıralayınız ( BETWEEN - AND yapısını kullanınız.)
  
  2. .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması 
  koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
  
  3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma 
  koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
*/


-- 1.SORU
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;

-- 2.SORU
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope','Nick','Ed');

-- 3.SORU
SELECT * FROM film
WHERE rental_rate IN (0.99,2.99,4.99) AND replacement_cost IN (12.99, 15.99, 28.99);

```

## ÖDEV 3 KOD:
```sql
/*
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1. country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri 
ile sonlananları sıralayınız.

2. country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri 
ile sonlananları sıralayınız.

3. film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri 
içeren film isimlerini sıralayınız.

4. film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan 
ve rental_rate 2.99 olan verileri sıralayınız.
*/

-- 1.SORU
SELECT * FROM country
WHERE country LIKE ('A%a');

-- 2.SORU
SELECT country FROM country
WHERE country LIKE ('______%m');

-- 3.SORU
SELECT title FROM film
WHERE title ILIKE ('%t%t%t%t');

-- 4.SORU
SELECT * FROM film
WHERE title LIKE('C%') AND length > 90 AND rental_rate IN(2.99);

```

## ÖDEV 4 KOD:
```sql
/*
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

    1. film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
    2. film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
    3. film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
    4. country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
    5. city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
*/

-- 1.SORU
SELECT DISTINCT replacement_cost FROM film;

-- 2.SORU
SELECT COUNT(DISTINCT replacement_cost) FROM film;

-- 3.SORU
SELECT COUNT(*) FROM film
WHERE title LIKE('T%') AND rating IN('G');

-- 4.SORU
SELECT COUNT(*) FROM country
WHERE country LIKE('_____');

-- 5.SORU
SELECT COUNT(*) FROM city
WHERE city LIKE('%R') OR city LIKE('%r');
```





