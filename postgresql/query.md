
### クエリのサイズ上限

- v9.5までは1G
- https://dba.stackexchange.com/questions/131399/is-there-a-maximum-length-constraint-for-a-postgres-query
- 最近のバージョンでは2G？
- https://stackoverflow.com/questions/4936731/maximum-length-of-an-sql-query

### Filter

- https://www.postgresql.org/docs/current/sql-expressions.html

```Example
SELECT
    count(*) AS unfiltered,
    count(*) FILTER (WHERE i < 5) AS filtered
FROM generate_series(1,10) AS s(i);
```

### 配列のカラム

- いくつかやり方がある
- https://www.postgresql.jp/document/7.2/user/arrays.html


```
CREATE TABLE sal_emp (
    name            text,
    pay_by_quarter  integer[]
);

// '{...}'
INSERT INTO sal_emp
    VALUES ('Bill',
    '{10000, 10000, 10000, 10000}');

// ARRAY[...]
INSERT INTO sal_emp
    VALUES ('Bill',
    ARRAY[10000, 10000, 10000, 10000]);
```

### jsonbカラムのlike

- https://stackoverflow.com/questions/42918348/postgresql-json-like-query
- `WHERE jsonbColumn->>'jsonAttr' LIKE '%foo%'`

