<template>

  <div class="home">
    <el-container>
     
      <el-header height="80px">
        <el-row :gutter="20">
          <el-col :span="4"><img src="../assets/logo.png" class="logo"/></el-col>
          <el-col :span="16">
            <el-menu
      :default-active="activeIndex"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
    >
      <el-menu-item index="1">Processing Center</el-menu-item>
      <el-sub-menu index="2">
        <template #title>Workspace</template>
        <el-menu-item index="2-1">item one</el-menu-item>
        <el-menu-item index="2-2">item two</el-menu-item>
        <el-menu-item index="2-3">item three</el-menu-item>
        <el-sub-menu index="2-4">
          <template #title>item four</template>
          <el-menu-item index="2-4-1">item one</el-menu-item>
          <el-menu-item index="2-4-2">item two</el-menu-item>
          <el-menu-item index="2-4-3">item three</el-menu-item>
        </el-sub-menu>
      </el-sub-menu>
      <el-menu-item index="3" disabled>Info</el-menu-item>
      <el-menu-item index="4">Orders</el-menu-item>
            </el-menu>
          </el-col>
          <el-col :span="4"><span class="quit-login">exit</span></el-col>
        </el-row>
    </el-header>
      <el-container>
        <el-aside width="200px">Aside</el-aside>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
    
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
/*
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
*/
export default defineComponent({
  name: 'HomeView',
  /*
  components: {
    HelloWorld,
  },*/
});
</script>

<style lang="scss" scoped>
.el-header{
  height: 80px;
  //background-color: aquamarine;
  .logo{
    height:80px;
  }
  h2,.quit-login{
    text-align: center;
    height:80px;
    line-height: 80px;
  }
}


</style>
<script lang="ts" setup>
import { ref } from 'vue'

const activeIndex = ref('1')
//const activeIndex2 = ref('1')
const handleSelect = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
</script>