<template>
  <div id="Goods">
    <el-row>
      <el-col :offset="1" :span="22">
        <tab-bar></tab-bar>
      </el-col>
    </el-row>

    <el-row justify="space-around" type="flex">
      <el-col :span="10">
        <act-list title="近期活动" style="height: 100%"></act-list>
      </el-col>
      <el-col :span="10">
        <new-list></new-list>
      </el-col>
    </el-row>

    <el-row justify="space-around" type="flex">
      <el-col  :span="10">
        <act-list title="推荐信息" :actImgs="imgList" style="height: 100%"></act-list>

      </el-col>
      <el-col :span="10">
        <new-list title="热点资讯"></new-list>
      </el-col>
    </el-row>

    <el-row>
      <el-col :offset="1" :span="22">
        <book-list img-height="50px" title="热门艺术"></book-list>
      </el-col>
    </el-row>
  </div>


</template>

<script>
import BookList from "@/components/BookList/BookList";
import ActList from "@/components/ActList/ActList";
import TabBar from "@/components/TabBar/TabBar";
import NewList from "@/components/NewsList/NewList";
import BookDetail from "@/components/bookDetail/BookDetail";

export default {
  data() {
    return {
      imgList: [
         require("@/assets/images/p4.png"),
         require("@/assets/images/p4.png"),
         require("@/assets/images/p4.png"),
         require("@/assets/images/p4.png"),
         require("@/assets/images/p4.png"),


      ]


    }
  },
  components: {
    NewList,
    BookList,
    ActList,
    TabBar,
    BookDetail
  }
}
</script>

<style scoped>

</style>
