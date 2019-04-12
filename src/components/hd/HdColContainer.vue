<template functional>
  <div class="hd-col-container">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "hd-col-container"
};
</script>

<style lang="scss" scoped>
.hd-col-container{
    display: flex;
    flex-direction: column;
    height: inherit;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
</style>