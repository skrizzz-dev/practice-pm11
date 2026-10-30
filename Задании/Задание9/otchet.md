Первый запрос: 
sqlite> SELECT * FROM product WHERE price > 100;
4|Сыр|200|
5|Чай|150|2

Второй запрос: 
sqlite> SELECT * FROM product WHERE price BETWEEN 50 AND 200;
2|Мыло|80|2
3|Молоко|60|1
4|Сыр|200|
5|Чай|150|2

Третий запрос:
sqlite> SELECT * FROM product WHERE name LIKE 'Х%';
1|Хлеб|40|1

Четвертый запрос:
sqlite> SELECT * FROM product WHERE category_id IS NULL;
4|Сыр|200|

Пятый запрос:
sqlite> SELECT * FROM product ORDER BY price DESC;
4|Сыр|200|
5|Чай|150|2
2|Мыло|80|2
3|Молоко|60|1
1|Хлеб|40|1

Шестой запрос:
sqlite> SELECT * FROM product LIMIT 3;
1|Хлеб|40|1
2|Мыло|80|2
3|Молоко|60|1

Седьмой запрос:
sqlite> SELECT * FROM product WHERE price % 10 = 0;
1|Хлеб|40|1
2|Мыло|80|2
3|Молоко|60|1
4|Сыр|200|
5|Чай|150|2

Восьмой запрос:
sqlite> SELECT * FROM product WHERE name LIKE '%о%';
2|Мыло|80|2
3|Молоко|60|1

Девятый запрос:
sqlite> SELECT * FROM product WHERE price > (SELECT AVG(price) FROM product) A
ND category_id IS NOT NULL ORDER BY price DESC LIMIT 5;
5|Чай|150|2