<template>
  <div>
    <h2>Vue-Core-Concepts-Demo</h2>
    <el-row class="el-row-height">
      <el-col :span="24">
        <BlogPost
          title="My Blog1"
          :postFontSize="postFontSize1"
          @enlarge-text="postFontSize1 += 0.1"
        >...content1...</BlogPost>
        <BlogPost
          title="My Blog2"
          :postFontSize="postFontSize2"
          @enlarge-text="postFontSize2 += 0.1"
          :showButton="false"
        >...content2...</BlogPost>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import BlogPost from "../components/BlogPost.vue";

export default {
  name: "EventDemo",
  components: {
    BlogPost
  },
  data() {
    return {
      postFontSize1: 1,
      postFontSize2: 1
    };
  }
};
</script>

<style lang="scss" scoped>
</style>

