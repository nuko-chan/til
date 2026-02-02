## 実務における使い分けのイメージ

- 両方のテーブルに一致するものだけが欲しい -> INNER JOIN
- 片方（たとえばユーザー）を全部出して、もう片方の有無を見たい -> LEFT JOIN

## サンプル

users テーブル

| id  | name |
| --- | ---- |
| 1   | 山田 |
| 2   | 佐藤 |
| 3   | 鈴木 |

orders テーブル

| id  | user_id | amount |
| --- | ------- | ------ |
| 101 | 1       | 5000   |
| 102 | 2       | 3000   |
| 103 | 4       | 7000   |

## INNER JOIN

両方に一致するデータだけを取得

```sql
SELECT
  users.id AS user_id,
  users.name,
  orders.id AS order_id,
  orders.amount
FROM users
INNER JOIN orders
  ON users.id = orders.user_id;
```

結果:

| user_id | name | order_id | amount |
| ------- | ---- | -------- | ------ |
| 1       | 山田 | 101      | 5000   |
| 2       | 佐藤 | 102      | 3000   |

## LEFT JOIN

左のテーブルは全て表示、右がなければ NULL

```sql
SELECT
  users.id AS user_id,
  users.name,
  orders.id AS order_id,
  orders.amount
FROM users
LEFT JOIN orders
  ON users.id = orders.user_id;
```

結果:

| user_id | name | order_id | amount |
| ------- | ---- | -------- | ------ |
| 1       | 山田 | 101      | 5000   |
| 2       | 佐藤 | 102      | 3000   |
| 3       | 鈴木 | NULL     | NULL   |
