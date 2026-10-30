Первый запрос:
sqlite> SELECT p.name, c.name FROM product p INNER JOIN category c ON p.category_id = c.id;
Хлеб|Еда
Мыло|Быт
Молоко|Еда

Второй запрос:
sqlite> SELECT p.name, c.name FROM product p LEFT  JOIN category c ON p.catego
ry_id = c.id;
Хлеб|Еда
Мыло|Быт
Молоко|Еда
Сыр|

Третий запрос:
sqlite> SELECT p.name, c.name FROM product p LEFT  JOIN category c ON p.category_id = c.id WHERE p.category_id IS NULL;
Сыр|

Четвертый запрос:
sqlite> SELECT c.id, c.name, COUNT(p.id) AS cnt FROM category c LEFT JOIN prod
uct p  ON p.category_id = c.id GROUP BY c.id, c.name;
1|Еда|2
2|Быт|1
3|Напитки|0

Пятый запрос:
sqlite> SELECT p.name, c.name FROM product p FULL JOIN category c ON p.categor
y_id = c.id;
Хлеб|Еда
Мыло|Быт
Молоко|Еда
Сыр|
|Напитки

Шестой запрос:
sqlite> SELECT c.id, c.name FROM category c LEFT JOIN product p ON p.category_id = c.id WHERE p.id IS NULL;
3|Напитки

Седьмой запрос:
sqlite> SELECT p.id, p.name AS product, p.price, c.name AS category, s.name as supplier FROM product p JOIN category c ON p.category_id = c.id JOIN supplier s ON p.supplier_id = s.id;
1|Хлеб|40|Еда|ООО Хлебозавод
2|Мыло|80|Быт|ИП Иванов
3|Молоко|60|Еда|ООО Хлебозавод

Восмьой запрос:
sqlite> SELECT p.name FROM product p JOIN category c ON p.category_id = c.id WHERE c.name LIKE 'Е%';
Хлеб
Молок