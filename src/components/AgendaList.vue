<script setup>
import AgendaItem from './AgendaItem.vue';
import { defineProps } from 'vue';

const props = defineProps({
  current: {
    type: Object,
    required: true
  },
  waiting: {
    type: Array,
    required: true
  }
});
</script>

<template>
  <div class="agenda-list">
    <section class="current-section">
      <div class="section-header">
        <div class="status-dot"></div>
        <h2>正在讨论 (已签到: {{ current.checkedInCount }}/{{ current.totalCount }})</h2>
      </div>
      <AgendaItem 
        :item="current"
        :isCurrent="true"
      />
    </section>

    <section class="waiting-section">
      <div class="section-header">
        <div class="status-dot waiting"></div>
        <h2>等待讨论 ({{ waiting.length }}个议题)</h2>
      </div>
      <AgendaItem 
        v-for="(item, index) in waiting"
        :key="index"
        :item="item"
        :isCurrent="false"
      />
    </section>
  </div>
</template>

<style scoped>
.agenda-list {
  background: #f5f5f5;
  border-radius: 8px;
  padding: 20px;
}

.section-header {
  display: flex;
  align-items: center;
  margin-bottom: 16px;
}

.status-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #4CAF50;
  margin-right: 8px;
}

.status-dot.waiting {
  background: #FFA000;
}

h2 {
  font-size: 16px;
  color: #333;
  margin: 0;
}

.current-section {
  margin-bottom: 30px;
}
</style>