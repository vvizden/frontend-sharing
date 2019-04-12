<template functional>
  <div class="hd-form">
    <header class="caption" v-if="caption">{{caption}}</header>
    <div class="table-part">
      <table class="table-format" :style="tableStyle">
        <tbody>
          <slot></slot>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "hd-form",
  props: {
    caption: String,
    tableStyle: [String, Object, Array]
  }
};
</script>

<style lang="scss" scoped>
.hd-form {
  display: flex;
  flex-direction: column;
  height: inherit;
  max-height: 100%;
  padding: 0 0 16px;
  border: 1px solid #cfdcf5;
  box-sizing: border-box;

  .caption {
    box-sizing: border-box;
    border-bottom: 1px solid #cfdcf5;
    padding-left: 16px;
    padding-right: 16px;
    text-align: left;
    font-size: 13px;
    color: #202325;
    height: 30px;
    background-color: #ebf1fd;
  }

  .table-part {
    padding: 16px 16px 0;
    overflow-y: scroll;
    box-sizing: border-box;

    .table-format {
      width: 100%;
      height: auto;
      border-collapse: collapse;
      text-align: left;
    }
  }
}
</style>

