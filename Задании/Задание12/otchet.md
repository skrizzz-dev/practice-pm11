Первый запрос:
sqlite> SELECT * FROM product WHERE price > (SELECT AVG(price) FROM product);
4|Сыр|200||3

Второй запрос:
sqlite> SELECT * FROM product WHERE category_id = (SELECT id FROM category WHERE name LIKE 'Еда');
1|Хлеб|40|1|1
3|Молоко|60|1|1

Третий запрос:
sqlite> SELECT c.id, c.name FROM category c WHERE EXISTS (SELECT 1 FROM produc
t p WHERE p.category_id = c.id);
1|Еда
2|Быт

Четвертый запрос
sqlite> SELECT c.id, c.name FROM category c WHERE NOT EXISTS (SELECT 1 FROM pr
oduct p WHERE p.category_id = c.id);
3|Напитки

Пятый запрос:
sqlite> SELECT * FROM product WHERE price = (SELECT MAX(price) FROM product);
4|Сыр|200||3

Шестой запрос:
sqlite> SELECT * FROM product p WHERE price  > (SELECT AVG(price) FROM product
  WHERE category_id = p.category_id);
3|Молоко|60|1|1

Седьмой запрос:
sqlite> SELECT * FROM product p WHERE price  > (SELECT MAX(price) FROM product
  WHERE category_id = 2);
4|Сыр|200||3

Восмьой запрос:
SELECT c.id, c.name FROM category c JOIN product p ON p.category_id = c.id GROUP BY c.id, c.name HAVING AVG(price) > 100;