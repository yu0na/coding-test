# json-server 쿼리 활용 가이드

json-server가 제공하는 쿼리 기능을 활용하여 페이지네이션, 정렬, 날짜 필터를 구현할 수 있습니다.

<br/>

### 1. 페이지네이션(Infinite Scroll)
아래 쿼리를 사용해 페이지 단위로 데이터를 조회할 수 있습니다.
```sql
    GET /campaigns?_page=1&_limit=1
```

- `_page` : 페이지 번호 (1부터 시작)
- `_limit` : 페이지 당 아이템 수
- 응답 헤더의 `X-Total-Count` 값을 활용해 추가 데이터가 있는지 여부를 판단할 수 있습니다.
 