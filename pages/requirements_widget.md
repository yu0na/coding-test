---
layout: two-cols
layoutClass: gap-8
---

# 구현 요구사항
### Pivot Table Widget (필수)

<br/>

<TablePreview
  :highlightHeader="true"
/>

::right::

<div class="requirements-content">

<br/>
<br/>
<br/>
<br/>
<br/>

마케팅/성과 데이터를 보여주는 <strong>Pivot Table Widget</strong> 을 구현합니다.

1. 첫 번째 행
    - `name`을 표시합니다.
2. 나머지 행
    - 아래 <strong>필수 메트릭</strong>을 반드시 테이블에 포함해서 표시합니다.
    - `clicks`, `dailyBudgetAmount`, `impressions`, `lifeTimeBudgetAmount`, `spend`, `channel`, `cpc`, `cpm`, `ctr`, `cvr`, `cpr`,
    - 숫자 값은 BI UI에 적절한 포맷으로 표현해 주세요.(타입 정보는 GET /types API를 참고해 주세요.)
    - 퍼센트 값의 경우, * 100을 적용하여 표시해 주세요.

</div>

<style>
.requirements-content {
  font-size: 0.85em;
}

.requirements-content h2 {
  font-size: 1.3em;
  margin-bottom: 0.5em;
  color: #4EC5D4;
}
</style>


