<script setup lang="ts">
const isCollapse = ref(false);
const handleOpen = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
const handleClose = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
</script>

<template>
  <div h100vh w100vw flex overflow-hidden>
    <el-container>
      <el-aside :width="!isCollapse ? '200px' : '64px'" bg-gray-700 text-center>
        <div py-4 text-white flex flex-row items-center justify-center gap-2>
          <div i-carbon:gui-management></div>
          <div v-show="!isCollapse">后台管理</div>
        </div>
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
</style>
