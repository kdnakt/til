
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
