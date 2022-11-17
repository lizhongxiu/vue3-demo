<template>
  <div class="common-layout">
    <div class="header">
      <el-radio-group v-model="isCollapse" style="margin-bottom: 20px">
        <el-radio-button :label="false">expand</el-radio-button>
        <el-radio-button :label="true">collapse</el-radio-button>
      </el-radio-group>
    </div>
    <el-container>
      <el-container>
        <el-aside :width="width" class="left">
          <el-col>
            <el-menu
              default-active="2"
              class="el-menu-vertical-demo"
              :collapse="isCollapse"
              @open="() => {}"
              @close="() => {}"
            >
              <el-sub-menu index="1">
                <template #title>
                  <el-icon><icon-menu /></el-icon>
                  <span>Navigator One</span>
                </template>
                <el-menu-item-group>
                  <el-menu-item index="1-1">item one</el-menu-item>
                  <el-menu-item index="1-2">item two</el-menu-item>
                </el-menu-item-group>
                <el-menu-item-group>
                  <el-menu-item index="1-3">item three</el-menu-item>
                </el-menu-item-group>
                <el-sub-menu index="1-4">
                  <template #title>item four</template>
                  <el-menu-item index="1-4-1">item one</el-menu-item>
                </el-sub-menu>
              </el-sub-menu>
              <el-menu-item index="2">
                <el-icon><icon-menu /></el-icon>
                <template #title>Navigator Two</template>
              </el-menu-item>
              <el-menu-item index="3" disabled>
                <el-icon><icon-menu /></el-icon>
                <template #title>Navigator Three</template>
              </el-menu-item>
              <el-menu-item index="4">
                <el-icon><setting /></el-icon>
                <template #title>Navigator Four</template>
              </el-menu-item>
            </el-menu>
          </el-col>
        </el-aside>
        <el-container>
          <el-main class="main text-red-500">
            <div v-for="item in 200" :key="item" class="btn-indigo mb-5">
              {{ item }}
            </div>
          </el-main>
        </el-container>
      </el-container>
    </el-container>
  </div>
</template>

<script lang="ts" setup>
import { computed, reactive, ref } from "vue";
import { Menu as IconMenu, Setting } from "@element-plus/icons-vue";
const a = ref<string>("23234");
const b = reactive({
  a1: 12312,
  b1: 33333,
});
const isCollapse = ref<boolean>(false);
const width = computed(() => {
  if (isCollapse.value) {
    return "65px";
  } else {
    return "200px";
  }
});
console.log(a.value, b);
</script>
<style lang="scss" scoped>
.header {
  background-color: rgb(37, 34, 34);
  color: #fff;
  height: 80px;
}
.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 200px;
  min-height: 400px;
}
.el-menu {
  border: 0;
}
.left {
  height: calc(100vh - (80px));
  background-color: #fff;
}
.main {
  margin: 20px;
  background-color: #f4f4f4;
  border-radius: 10px;
  overflow: auto;
  height: calc(100vh - (120px));
}
.btn-indigo {
  @apply py-2 px-4 text-center bg-gray-50 text-red-500 font-semibold rounded-lg shadow-md hover:bg-indigo-700 focus:outline-none focus:ring-indigo-400 focus:ring-opacity-75;
}
</style>
