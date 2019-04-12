<template>
  <div>
    <h2>Flex-Demo</h2>
    <el-row :gutter="16" class="el-row-height">
      <el-col :span="12">
        <div class="flex-box-row wrapper">
          <div class="flex-item"></div>
          <div class="flex-item bkgc-diff"></div>
          <div class="flex-item"></div>
          <div class="flex-item bkgc-diff"></div>
        </div>
      </el-col>
      <el-col :span="12">
        <div class="flex-box-col wrapper">
          <div class="flex-item"></div>
          <div class="flex-item bkgc-diff"></div>
          <div class="flex-item"></div>
          <div class="flex-item bkgc-diff"></div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "FlexDemo"
};
</script>

<style lang="scss" scoped>
.wrapper {
  height: inherit;
  border: 1px solid cornflowerblue;
}

.flex-item {
  min-width: 100px;
  min-height: 100px;
  background-color: burlywood;
}

.bkgc-diff {
  background-color: brown;
}
</style>

