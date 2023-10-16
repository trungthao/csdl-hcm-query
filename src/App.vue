<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue';
import TeachingAssignmentView from './views/TeachingAssignmentView.vue'
import SelectOrganization from './components/SelectOrganization.vue';

const currOrganization = ref({});
const activeKey = ref('1');

function handleSelectOrganization(curOrg) {
  console.log(currOrganization);
}
</script>

<template>
  <SelectOrganization v-model="currOrganization" @selected-org="handleSelectOrganization" />
  <a-tabs v-model:activeKey="activeKey">
    <a-tab-pane key="1" tab="Tab 1">
      <TeachingAssignmentView />
    </a-tab-pane>
    <a-tab-pane key="2" tab="Tab 2" force-render>Content of Tab Pane 2</a-tab-pane>
    <a-tab-pane key="3" tab="Tab 3">Content of Tab Pane 3</a-tab-pane>
  </a-tabs>

  <!-- <RouterView /> -->
</template>

<style scoped></style>
