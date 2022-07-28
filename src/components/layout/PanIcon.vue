<script setup lang="ts">
defineProps({
  size: {
    type: Number,
    default: 24,
  },
  icon: {
    type: String,
    required: true
  }
})
</script>

<template>
  <el-icon :size="size">
    <Component :is="icon" />
  </el-icon>
</template>
