<script setup lang="ts">
const isCollapse = ref(false);
const handleOpen = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
const handleClose = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
const collapse = computed(() => {
  return isCollapse.value ? '64px' : '200px'
})
</script>

<template>
  <div h100vh w100vw flex overflow-hidden>
    <el-container>
      <el-aside :width="collapse" bg-gray-700 text-center>
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
        <el-scrollbar>
          <el-menu default-active="1" :collapse="isCollapse" active-text-color="#4169e1" background-color="#374151"
            text-color="#fff" @open="handleOpen" @close="handleClose">
            <el-menu-item index="1">
              <el-icon>
                <document />
              </el-icon>
              <template #title>Navigator 1</template>
            </el-menu-item>
            <el-menu-item index="2">
              <el-icon>
                <setting />
              </el-icon>
              <template #title>Navigator 2</template>
            </el-menu-item>
          </el-menu>
        </el-scrollbar>
      </el-aside>
      <el-container>
        <el-header bg-blue flex flex-row gap-4px items-center>
          <el-icon @click="isCollapse = !isCollapse" :size="32">
            <Component :is="isCollapse ? 'Expand' : 'Fold'" />
          </el-icon>
        </el-header>
        <el-main bg-green>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<style scoped>
.el-menu {
  border: none;
}

.el-aside {
  overflow: hidden;
  transition: ease-in-out 0.3s;
  transition-timing-function: ease-in-out;
}

.sidebarLogoFade-enter-active {
  transition: opacity 1.5s;
}

.sidebarLogoFade-enter,
.sidebarLogoFade-leave-to {
  opacity: 0;
}
</style>
