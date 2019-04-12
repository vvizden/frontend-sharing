<template functional>
  <tr v-if="dataNonEmpty">
    <template v-if="isArray">
      <template v-for="item of data">
        <th :style="item[dataMap['lableStyle']]">{{item[dataMap['lable']]}}</th>
        <td :style="item[dataMap['valueStyle']]">{{item[dataMap['value']]}}</td>
      </template>
    </template>
    <template v-else>
      <th :style="data[dataMap['lableStyle']]">{{data[dataMap['lable']]}}</th>
      <td :style="data[dataMap['valueStyle']]">{{data[dataMap['value']]}}</td>
    </template>
  </tr>
</template>

<script>
export default {
  name: "hd-form-item",
  props: {
    data: [Array, Object],
    dataMap: {
      type: Object,
      default() {
        return {
          lable: "lable",
          value: "value",
          lableStyle: 'lableStyle',
          valueStyle: 'valueStyle'
        };
      }
    }
  },
  computed: {
    isArray() {
      return Array.isArray(this.data);
    },
    dataNonEmpty() {
      if (this.isArray) {
        return this.data.length > 0;
      }
      if (Object.prototype.toString.call(this.data) === "[object Object]") {
        return Object.keys(this.data).length > 0;
      }
      return false;
    }
  }
};
</script>

<style lang="scss" scoped>
th,
td {
  box-sizing: border-box;
  border: 1px solid #cfdcf5;
  padding-left: 8px;
  padding-right: 8px;
  font-size: 12px;
}

th {
  background-color: #f9f9f9;
}
</style>

