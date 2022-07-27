<script setup lang="ts">
defineProps({
  isCollapse: {
    type: Boolean,
    required: true
  },
})
</script>

<template>
  <div class="sidebar-logo-container" flex items-center justify-center text-white py-18px>
    <transition name="sidebarLogoFade">
      <router-link v-if="isCollapse" key="collapse" to="/">
        <div i-carbon:gui-management text-white></div>
      </router-link>
      <router-link v-else key="expand" to="/" flex flex-row>
        <div i-carbon:gui-management mr-12px text-5></div>
        <h1 class="sidebar-title">后台管理</h1>
      </router-link>
    </transition>
  </div>
</template>
