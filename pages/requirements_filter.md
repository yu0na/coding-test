---
layout: two-cols
layoutClass: gap-8
---

# 구현 요구사항
### 필터 (필수)

<br/>

<TablePreview
  :highlightFilter="true"
/>

::right::

<div class="requirements-content">

<br/>
<br/>
<br/>
<br/>
<br/>

<strong>Dropdown UI</strong>를 사용하여 필터를 구현합니다.

- **필터 옵션**
    - Last week
    - Last month
    - Last year

- **필터 옵션 변경 시,**
    - 테이블은 <strong>1 페이지 상태로 리셋</strong>되어야 합니다.
    - 변경된 조건 기준으로 <strong>API를 다시 호출</strong>해야 합니다.

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