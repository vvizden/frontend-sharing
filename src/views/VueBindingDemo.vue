<template>
  <div>
    <h2>Vue-Binding-Demo</h2>
    <el-row :gutter="16" class="el-row-height">
      <el-col :span="12">
        <h3>Vue单向数据流与双向绑定</h3>
        <input type="text" :value="value" @input="value = $event.target.value">
        <div>{{value}}</div>
      </el-col>
      <el-col :span="12">
        <h3>数据驱动视图的原理</h3>
        <input ref="input" type="text" @input="handleInput($event)">
        <div ref="inputValue"></div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
let dataCopy;
export default {
  name: "VueBindingDemo",
  data() {
    return {
      value: ""
    };
  },
  mounted() {
    const that = this;
    dataCopy = {
      _value1: "",
      get value1() {
        return this._value1;
      },
      set value1(val) {
        this._value1 = val;
        that.$refs.input.value = this._value1;
        that.$refs.inputValue.innerHTML = this._value1;
      }
    };
  },
  methods: {
    handleInput(event) {
      dataCopy.value1 = event.target.value;
    }
  }
};
</script>

<style lang="scss" scoped>
</style>

