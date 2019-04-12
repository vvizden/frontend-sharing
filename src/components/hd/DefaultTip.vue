<template functional>
  <span class="default-tip">{{props.text}}</span>
</template>

<script>
export default {
  name: "hd-default-tip",
  props: {
    text: {
      type: String,
      default() {
        return "暂无数据";
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.default-tip {
  font-size: 12px;
  font-weight: 600;
  color: #909399;
}
</style>
