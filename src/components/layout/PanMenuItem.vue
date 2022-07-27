<script setup lang="ts">
interface item {
  name: string;
  path: string;
  icon?: string;
  children?: item[];
}
defineProps({
  routes: {
    type: Array<item>,
    required: true
  },
})
</script>

<template>
  <template v-for="item in routes" :key="item.name">
    <el-menu-item :index="item.path" v-if="!item.children">
      <PanIcon :icon="item.icon" v-if="item.icon" />
      <template #title>{{ item.name }}</template>
    </el-menu-item>
    <el-sub-menu :index="item.path" v-else>
      <template #title>
        <PanIcon :icon="item.icon" v-if="item.icon" />
        <span>{{ item.name }}</span>
      </template>
      <el-menu-item :index="childrenItem.path" v-for="childrenItem in item.children" :key="childrenItem.name">
        <PanIcon :icon="item.icon" v-if="item.icon" />
        <template #title>{{ childrenItem.name }}</template>
      </el-menu-item>
    </el-sub-menu>
  </template>
</template>
