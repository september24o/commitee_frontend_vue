<script setup>
import { ref } from 'vue';
import AgendaList from './components/AgendaList.vue';

const meetingData = ref({
  current: {
    title: "2024年第一季度预算审批",
    proposingDept: "财务部",
    attendingDepts: [
      { name: "人力资源部", checkedIn: true },
      { name: "运营部", checkedIn: true },
      { name: "技术部", checkedIn: true }
    ],
    startTime: "14:30",
    checkedInCount: 3,
    totalCount: 4
  },
  waiting: [
    {
      title: "新产品发布计划讨论",
      proposingDept: "产品部",
      attendingDepts: [
        { name: "市场部", checkedIn: false },
        { name: "技术部", checkedIn: false },
        { name: "销售部", checkedIn: false }
      ],
      checkedInCount: 0,
      totalCount: 4
    },
    {
      title: "员工培训方案评审",
      proposingDept: "人力资源部",
      attendingDepts: [
        { name: "培训部", checkedIn: false },
        { name: "各部门主管", checkedIn: false }
      ],
      checkedInCount: 0,
      totalCount: 3
    },
    {
      title: "办公室搬迁方案",
      proposingDept: "行政部",
      attendingDepts: [
        { name: "财务部", checkedIn: false },
        { name: "人力资源部", checkedIn: false }
      ],
      checkedInCount: 0,
      totalCount: 3
    }
  ]
});
</script>

<template>
  <div class="meeting-container">
    <h1>会议议题队列</h1>
    <AgendaList 
      :current="meetingData.current"
      :waiting="meetingData.waiting"
    />
  </div>
</template>

<style>
.meeting-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  color: #333;
  font-size: 24px;
  margin-bottom: 20px;
}
</style>