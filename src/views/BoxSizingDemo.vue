<template>
  <div>
    <h2>Box-Sizing-demo</h2>
    <el-row :gutter="16" class="el-row-height">
      <el-col :span="12">
        <ModuleContainer header="标题一">
          <DefaultTip/>
        </ModuleContainer>
      </el-col>
      <el-col :span="12">
        <ModuleContainer header="标题二">
          <DefaultTip/>
        </ModuleContainer>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import ModuleContainer from "../components/hd/ModuleContainer.vue";
import DefaultTip from "../components/hd/DefaultTip.vue";

export default {
  components: {
    ModuleContainer,
    DefaultTip
  }
};
</script>

<style lang="scss" scoped>
</style>