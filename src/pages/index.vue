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
const routes = ref([
  {
    name: 'one',
    path: '/one',
    icon: 'document',
  },
  {
    name: 'two',
    path: '/two',
    icon: 'setting',
  },
  {
    name: 'three',
    path: '/three',
    icon: 'setting',
    children: [
      {
        name: 'three-one',
        path: '/three/one',
        icon: 'document',
      },
      {
        name: 'three-two',
        path: '/three/two',
        icon: 'setting',
      },
    ]
  },
])
</script>

<template>
  <div h100vh w100vw flex overflow-hidden>
    <el-container>
      <el-aside :width="collapse" bg-gray-700 text-center>
        <PanLogo :isCollapse="isCollapse" />
        <el-scrollbar>
          <el-menu default-active="1" :collapse="isCollapse" active-text-color="#4169e1" background-color="#374151"
            text-color="#fff" @open="handleOpen" @close="handleClose">
            <PanMenuItem :routes="routes" />
          </el-menu>
        </el-scrollbar>
      </el-aside>
      <el-container>
        <el-header bg-blue flex flex-row gap-4px items-center>
          <PanIcon :icon="isCollapse ? 'Expand' : 'Fold'" @click="isCollapse = !isCollapse" />
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
