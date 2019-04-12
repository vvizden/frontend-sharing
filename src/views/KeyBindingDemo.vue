<template>
  <div>
    <h2>Key-Binding-Demo</h2>
    <el-row class="el-row-height">
      <el-col :span="24">
        <div v-for="(key, index) in list" :key="index">
          <input type="text">
          <button @click.stop.prevent="handlerDelete(key)">删除</button>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "EventDemo",
  data() {
    return {
      list: [1,2,3]
    };
  },
  methods: {
    handlerDelete(key) {
      const index = this.list.findIndex(e => e === key);
      this.list.splice(index, 1);
    }
  }
};
</script>

<style lang="scss" scoped>
</style>