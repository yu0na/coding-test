# json-server 쿼리 활용 가이드

### 3. 날짜 필터(Range Query)

날짜 범위를 기준으로 데이터를 필터링할 수 있습니다.

```sql
GET /campaigns?from_gte=2023-08-16&to_lte=2023-09-14
```

- `_gte` : 이상
- `_lte` : 이하

Last week / Last month / Last year 옵션은 클라이언트에서 날짜 범위를 계산한 후, 
해당 값을 쿼리 파라미터로 변환해 전달해 주세요.