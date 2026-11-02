Первый запрос:
CREATE TABLE product (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    price REAL NOT NULL CHECK (price >= 0)
);

Второй запрос:
CREATE TABLE product (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL UNIQUE,
    price REAL NOT NULL CHECK (price >= 0)
);

Третий запрос:
sqlite> SELECT *, CASE 
   ...> WHEN price > 100 THEN 'дорого' 
   ...> WHEN price < 50 THEN 'дешёво' 
   ...> END
   ...> FROM product;

Четвертый запрос:
sqlite> UPDATE product           
   ...> SET category_id = COALESCE(category_id, 0)
   ...> WHERE category_id IS NULL;

Пятый запрос: 
SELECT 100 / NULLIF(price, 0) FROM product;

Шестой запрос:
CREATE TABLE product (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL UNIQUE,
    price REAL DEFAULT 0 NOT NULL CHECK (price >= 0)
);

Седьмой запрос:
sqlite> SELECT name, CASE
   ...> WHEN price > 100 THEN 'дорого'
   ...> WHEN price > 50 THEN 'среднее'
   ...> ELSE 'дешёво'        
   ...> END AS price_category 
   ...> from product; 

╭────────┬──────────────────────╮
│  name  │ CASE WHEN price >... │
╞════════╪══════════════════════╡
│ Хлеб   │ дешёво               │
│ Мыло   │ среднее              │
│ Молоко │ среднее              │
│ Сыр    │ дорого               │
╰────────┴──────────────────────╯

Восьмой вопрос:
sqlite> SELECT id, name, price, discount, COALESCE(price, 0) - COALESCE(discount, 0) AS total FROM product;
╭────┬────────┬───────┬──────────┬───────╮
│ id │  name  │ price │ discount │ total │
╞════╪════════╪═══════╪══════════╪═══════╡
│  1 │ Хлеб   │    40 │     10.5 │  29.5 │
│  2 │ Мыло   │    80 │ NULL     │    80 │
│  3 │ Молоко │    60 │      0.0 │  60.0 │
│  4 │ Сыр    │   200 │     15.0 │ 185.0 │
╰────┴────────┴───────┴──────────┴───────╯