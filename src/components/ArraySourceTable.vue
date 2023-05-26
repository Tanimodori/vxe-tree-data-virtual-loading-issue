<template>
  <div>
    <vxe-toolbar>
      <template #buttons>
        <vxe-button @click="expandAllEvent">展开所有</vxe-button>
        <vxe-button @click="claseExpandEvent">收起所有</vxe-button>
        &nbsp; ArraySourceTable.vue
      </template>
    </vxe-toolbar>

    <vxe-table
      ref="xTreeRef"
      show-overflow
      height="400"
      :tree-config="{ transform: true }"
      :scroll-y="{ gt: 20 }"
      :data="data"
    >
      <vxe-column type="seq" width="200" tree-node></vxe-column>
      <vxe-column field="name" title="Name"></vxe-column>
      <vxe-column field="size" title="Size"></vxe-column>
      <vxe-column field="type" title="Type"></vxe-column>
      <vxe-column field="date" title="Date"></vxe-column>
    </vxe-table>
  </div>
</template>

<script lang="ts" setup>
  import { ref } from 'vue'
  import type { VxeTableInstance } from 'vxe-table'
  import { getData } from './data'

  const xTreeRef = ref<VxeTableInstance>()

  const expandAllEvent = () => {
    const $table = xTreeRef.value
    if ($table) {
      $table.setAllTreeExpand(true)
    }
  }

  const claseExpandEvent = () => {
    const $table = xTreeRef.value
    if ($table) {
      $table.clearTreeExpand()
    }
  }

  const data = ref(getData())
</script>
