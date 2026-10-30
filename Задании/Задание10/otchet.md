Первый запрос:
sqlite> SELECT COUNT(*) FROM product;
4

Второй запрос:
sqlite> SELECT AVG(price) FROM product;
95.0

Третий запрос:
sqlite> SELECT category_id, COUNT(*) FROM product GROUP BY category_id;
|1
1|2
2|1

Четвертый запрос:
sqlite> SELECT category_id, SUM(price) FROM product GROUP BY category_id;
|200
1|100
2|80

Пятый запрос:
sqlite> SELECT category_id, COUNT(*) FROM product GROUP BY category_id HAVING COUNT(*) > 2;

Шестой запрос:
sqlite> SELECT MAX(price), MIN(price) FROM product;
200|40

Седьмой запрос:
sqlite> SELECT category_id, COUNT(*) FROM product GROUP BY category_id HAVING 
AVG(price) > 100;
|1

Восьмой запрос:
sqlite> SELECT * FROM product WHERE price > (SELECT AVG(price) FROM product);
4|Сыр|200|

Девятый запрос:
sqlite> SELECT category_id, COUNT(price), AVG(price), MAX(price) FROM product GROUP BY category_id;
|1|200.0|200
1|2|50.0|60
2|1|80.0|80