<template>
  <el-container style="height: 100vh">
    <el-aside
      :width="sideWidth + 'px'"
      style="
        background-color: rgb(238, 241, 246);
        box-shadow: 0px 0px 6px rgb(0, 21, 41);
      "
    >
      <Aside :isCollapse="isCollapse" :logoTextShow="logoTextShow"/>
    </el-aside>

    <el-container>
      <el-header
      style="border-bottom: 1px solid #ccc;">
      <Header :collapseBtnClass = "collapseBtnClass" :collapse="isCollapse" />
    </el-header>
      <el-main>
        <!-- 表示当前页面子路由会在router-view中展示 -->
        <router-view/>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>

import Aside from '@/components/Aside.vue';
import Header from '@/components/Header.vue';

export default {
  name: "Manage",
  components: {},
  data() {
    return {
      collapseBtnClass: "el-icon-s-fold",
      isCollapse: false,
      sideWidth: 200,
      logoTextShow: true,
    };
  },
  components:{
    Aside,
    Header
  },
  // created(){
  //   this.$router.push({
  //     path:'/user'
  //   })
  // },
  methods: {
    collapse() {
      // 点击收缩按钮触发
      this.isCollapse = !this.isCollapse;
      // 收缩
      if (this.isCollapse) {
        console.log(1111)
        this.sideWidth = 64;
        this.collapseBtnClass = "el-icon-s-unfold";
        this.logoTextShow = false;
        // 展开
      } else {
        this.sideWidth = 200;
        this.collapseBtnClass = "el-icon-s-fold";
        this.logoTextShow = true;
      }
    },
  },
  
};
</script>
