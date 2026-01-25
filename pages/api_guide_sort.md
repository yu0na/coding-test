# json-server 쿼리 활용 가이드

### 2. 정렬(Infinite Scroll)

특정 컬럼 기준으로 데이터를 정렬할 수 있습니다.

```sql
GET /campaigns?_sort=spend&_order=desc
```

- `_sort`: 정렬 기준 컬럼
- `_order`: 정렬 방향 (`asc` | `desc`)