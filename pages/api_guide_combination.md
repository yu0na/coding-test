# json-server 쿼리 활용 가이드


### 4. 필터 + 정렬 + 페이지네이션 조합 예시
아래는 날짜 필터, 정렬, 페이지네이션을 함께 적용한 예시입니다.
```sql
GET /campaigns
    ?from_gte=2023-08-16
    &to_lte=2023-09-14
    &_sort=spend
    &_order=desc
    &_page=1
    &_limit=10
```