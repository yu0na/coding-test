<script setup lang="ts">
const props = defineProps({
  highlightHeader: {
    type: Boolean,
    default: false,
  },
  highlightSort: {
    type: String,
    default: '', // 'name', 'clicks', etc.
  },
  sortDirection: {
    type: String,
    default: 'desc', // 'asc' or 'desc'
  },
  highlightFilter: {
    type: Boolean,
    default: false,
  },
  highlightScroll: {
    type: Boolean,
    default: false,
  },
  showUrlBar: {
    type: Boolean,
    default: false,
  },
  urlParams: {
    type: String,
    default: '',
  },
})

const sampleData = [
  { name: 'Campaign A', clicks: 1250, impressions: 50000, spend: 250.50, ctr: 2.5 },
  { name: 'Campaign B', clicks: 980, impressions: 42000, spend: 189.30, ctr: 2.33 },
  { name: 'Campaign C', clicks: 2100, impressions: 75000, spend: 420.00, ctr: 2.8 },
  { name: 'Campaign D', clicks: 750, impressions: 30000, spend: 150.00, ctr: 2.5 },
  { name: 'Campaign E', clicks: 1500, impressions: 60000, spend: 300.00, ctr: 2.5 },
]

const isColumnHighlighted = (column: string) => {
  return props.highlightSort === column
}
</script>

<template>
  <div class="table-preview-container">
    <!-- URL Bar (optional) -->
    <div v-if="showUrlBar" class="url-bar" :class="{ highlighted: highlightFilter || urlParams }">
      <div class="url-icon">🔗</div>
      <div class="url-text">
        example.com/dashboard<span v-if="urlParams" class="url-params">{{ urlParams }}</span>
      </div>
    </div>

    <!-- Filter Dropdown (optional) -->
    <div v-if="highlightFilter" class="filter-container highlighted">
      <select class="filter-dropdown">
        <option>Last week</option>
        <option>Last month</option>
        <option>Last year</option>
      </select>
    </div>

    <!-- Table Container -->
    <div class="table-wrapper" :class="{ 'highlight-scroll': highlightScroll }">
      <table class="pivot-table">
        <thead :class="{ highlighted: highlightHeader }">
          <tr>
            <th :class="{ 'sort-active': isColumnHighlighted('name') }">
              Name
              <span v-if="isColumnHighlighted('name')" class="sort-arrow">
                {{ sortDirection === 'desc' ? '↓' : '↑' }}
              </span>
            </th>
            <th :class="{ 'sort-active': isColumnHighlighted('clicks') }">
              Clicks
              <span v-if="isColumnHighlighted('clicks')" class="sort-arrow">
                {{ sortDirection === 'desc' ? '↓' : '↑' }}
              </span>
            </th>
            <th :class="{ 'sort-active': isColumnHighlighted('impressions') }">
              Impressions
              <span v-if="isColumnHighlighted('impressions')" class="sort-arrow">
                {{ sortDirection === 'desc' ? '↓' : '↑' }}
              </span>
            </th>
            <th :class="{ 'sort-active': isColumnHighlighted('spend') }">
              Spend
              <span v-if="isColumnHighlighted('spend')" class="sort-arrow">
                {{ sortDirection === 'desc' ? '↓' : '↑' }}
              </span>
            </th>
            <th :class="{ 'sort-active': isColumnHighlighted('ctr') }">
              CTR
              <span v-if="isColumnHighlighted('ctr')" class="sort-arrow">
                {{ sortDirection === 'desc' ? '↓' : '↑' }}
              </span>
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(row, index) in sampleData" :key="index">
            <td>{{ row.name }}</td>
            <td class="number">{{ row.clicks.toLocaleString() }}</td>
            <td class="number">{{ row.impressions.toLocaleString() }}</td>
            <td class="number">${{ row.spend.toFixed(2) }}</td>
            <td class="number">{{ row.ctr.toFixed(2) }}%</td>
          </tr>
        </tbody>
      </table>

      <!-- Scroll indicator -->
      <div v-if="highlightScroll" class="scroll-indicator">
        <div class="scroll-bar"></div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.table-preview-container {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 11px;
  background: #1e1e1e;
  border-radius: 8px;
  padding: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
  max-width: 100%;
  overflow: hidden;
}

.url-bar {
  background: #2d2d2d;
  border-radius: 4px;
  padding: 6px 10px;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  gap: 8px;
  border: 2px solid transparent;
  transition: all 0.3s ease;
}

.url-bar.highlighted {
  border-color: #4EC5D4;
  box-shadow: 0 0 0 2px rgba(78, 197, 212, 0.2);
  animation: pulse 2s ease-in-out infinite;
}

.url-icon {
  font-size: 12px;
}

.url-text {
  color: #888;
  font-family: 'Monaco', 'Menlo', monospace;
  font-size: 10px;
}

.url-params {
  color: #4EC5D4;
  font-weight: 600;
}

.filter-container {
  margin-bottom: 10px;
  border: 2px solid transparent;
  border-radius: 4px;
  padding: 4px;
  transition: all 0.3s ease;
}

.filter-container.highlighted {
  border-color: #4EC5D4;
  box-shadow: 0 0 0 2px rgba(78, 197, 212, 0.2);
  animation: pulse 2s ease-in-out infinite;
}

.filter-dropdown {
  width: 100%;
  background: #2d2d2d;
  color: #fff;
  border: 1px solid #444;
  border-radius: 4px;
  padding: 6px 10px;
  font-size: 11px;
  cursor: pointer;
}

.table-wrapper {
  position: relative;
  max-height: 200px;
  overflow-y: auto;
  border: 2px solid transparent;
  border-radius: 4px;
  transition: all 0.3s ease;
}

.table-wrapper.highlight-scroll {
  border-color: #4EC5D4;
  box-shadow: 0 0 0 2px rgba(78, 197, 212, 0.2);
  animation: pulse 2s ease-in-out infinite;
}

.pivot-table {
  width: 100%;
  border-collapse: collapse;
  background: #252525;
}

.pivot-table thead {
  position: sticky;
  top: 0;
  background: #2d2d2d;
  z-index: 10;
  border: 2px solid transparent;
  transition: all 0.3s ease;
}

.pivot-table thead.highlighted {
  border-color: #4EC5D4;
  box-shadow: 0 0 0 2px rgba(78, 197, 212, 0.2);
  animation: pulse 2s ease-in-out infinite;
}

.pivot-table th,
.pivot-table td {
  padding: 8px 10px;
  text-align: left;
  border-bottom: 1px solid #333;
  color: #ddd;
}

.pivot-table th {
  font-weight: 600;
  color: #fff;
  cursor: pointer;
  user-select: none;
  position: relative;
  transition: all 0.2s ease;
}

.pivot-table th:hover {
  background: #353535;
}

.pivot-table th.sort-active {
  background: #3d3d3d;
  color: #4EC5D4;
  border: 2px solid #4EC5D4;
  animation: pulse 2s ease-in-out infinite;
}

.sort-arrow {
  margin-left: 4px;
  font-size: 10px;
  color: #4EC5D4;
}

.pivot-table td.number {
  text-align: right;
  font-family: 'Monaco', 'Menlo', monospace;
}

.pivot-table tbody tr:hover {
  background: #2a2a2a;
}

.scroll-indicator {
  position: absolute;
  right: 2px;
  top: 40px;
  bottom: 2px;
  width: 6px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 3px;
}

.scroll-bar {
  width: 100%;
  height: 40%;
  background: #4EC5D4;
  border-radius: 3px;
  animation: scrollPulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% {
    box-shadow: 0 0 0 2px rgba(78, 197, 212, 0.2);
  }
  50% {
    box-shadow: 0 0 0 4px rgba(78, 197, 212, 0.4);
  }
}

@keyframes scrollPulse {
  0%, 100% {
    opacity: 0.6;
  }
  50% {
    opacity: 1;
  }
}
</style>
