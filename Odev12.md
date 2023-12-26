- Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
```SQL
SELECT COUNT (*) FROM film
WHERE length >
(
	SELECT AVG(length) from film
);
```

- Film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
```SQL
SELECT COUNT (*) FROM film
WHERE length = 
(
	SELECT MAX(length) from film
);
```
- Film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
```SQL
SELECT * from film
WHERE 
rental_rate = (SELECT MIN(rental_rate)from film) AND
replacement_cost = (SELECT MIN (replacement_cost) from film);
```
- Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
```SQL
SELECT customer.first_name, customer.last_name,COUNT(*) FROM customer
INNER JOIN payment ON customer.customer_id = payment.customer_id
GROUP BY customer.first_name, customer.last_name
ORDER BY COUNT(*) DESC; 
```