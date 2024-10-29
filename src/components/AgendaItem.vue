<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  item: {
    type: Object,
    required: true
  },
  isCurrent: {
    type: Boolean,
    default: false
  }
});
</script>

<template>
  <div class="agenda-item" :class="{ current: isCurrent }">
    <div class="agenda-header">
      <h3>{{ item.title }}</h3>
      <span v-if="isCurrent" class="start-time">
        开始时间: {{ item.startTime }}
      </span>
    </div>

    <div class="departments">
      <div class="dept-section">
        <span class="label">提出部门:</span>
        <span class="dept proposing">{{ item.proposingDept }}</span>
      </div>

      <div class="dept-section">
        <span class="label">列席部门:</span>
        <div class="attending-depts">
          <span 
            v-for="(dept, index) in item.attendingDepts" 
            :key="index"
            class="dept"
            :class="{ 'checked-in': dept.checkedIn }"
          >
            {{ dept.name }}
          </span>
        </div>
      </div>
    </div>

    <div class="check-in-status">
      已签到: {{ item.checkedInCount }}/{{ item.totalCount }}
    </div>
  </div>
</template>

<style scoped>
.agenda-item {
  background: white;
  border-radius: 8px;
  padding: 16px;
  margin-bottom: 16px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.agenda-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}

h3 {
  margin: 0;
  font-size: 16px;
  color: #333;
}

.start-time {
  color: #2196F3;
  font-size: 14px;
}

.departments {
  margin-bottom: 12px;
}

.dept-section {
  margin-bottom: 8px;
}

.label {
  color: #666;
  font-size: 14px;
  margin-right: 8px;
}

.dept {
  display: inline-block;
  padding: 4px 12px;
  border-radius: 16px;
  background: #f0f0f0;
  margin-right: 8px;
  margin-bottom: 8px;
  font-size: 14px;
}

.dept.proposing {
  background: #FFF3E0;
  color: #F57C00;
}

.dept.checked-in {
  background: #E8F5E9;
  color: #4CAF50;
}

.check-in-status {
  font-size: 14px;
  color: #666;
}

.current {
  border: 2px solid #E3F2FD;
}

.attending-depts {
  display: inline-block;
}
</style>