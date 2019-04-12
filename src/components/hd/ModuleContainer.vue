<template functional>
  <div class="module-container">
    <div class="module-header">{{props.header}}</div>
    <div class="module-body">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "hd-module-container",
  props: {
    header: {
      type: String
    }
  }
};
</script>

<style lang="scss" scoped>
.module-container {
  display: flex;
  flex-direction: column;
  height: inherit;
  max-height: 100%;
  box-sizing: border-box;
  border: 1px solid #cfdcf5;

  .module-header {
    box-sizing: border-box;
    padding: 0 16px;
    height: 30px;
    line-height: 30px;
    font-weight: normal;
    font-size: 13px;
    color: #202325;
    border-bottom: 1px solid #cfdcf5;
    background: #ebf1fd;
    flex: none;
  }

  .module-body {
    flex: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-y: scroll;
    padding: 8px 16px 0;
    margin-bottom: 8px;
    font-size: 12px;
  }
}
</style>

