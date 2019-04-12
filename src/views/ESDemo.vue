<template>
  <div>
    <h2>ES-Demo</h2>
    <el-row :gutter="16" class="el-row-height">
      <el-col :span="12">
        <h3>ES5</h3>
        <pre>
            <code>
                const set = [2, 13, 8, 53, 21, 6, 35];

                set.forEach(e => { console.log(e) });

                const setMap = set.map(e => e * 2);
                console.log(setMap);

                const setFiltered = set.filter(e => e > 8);
                console.log(setFiltered);

                const someGt50 = set.some(e => e > 50);
                console.log(someGt50);

                const everyGt50 = set.every(e => e > 50);
                console.log(everyGt50);

                const sum = set.reduce((last, e) => last + e, 0);
                console.log(sum);
            </code>
        </pre>
      </el-col>
      <el-col :span="12">
        <h3>ES6</h3>
        <h4>字符串模板</h4>
        <div>{{strTemplate}}</div>
        <h4>函数默认值</h4>
        <div>{{getFuncDefaultValue()}}</div>
        <h4>Object.assign()</h4>
        <div>{{assignObj}}</div>
        <h4>解构</h4>
        <div>{{getNameAndAge()}}</div>
        <h4>展开运算符</h4>
        <div>{{getNameAndCareer()}}</div>
        <div>{{getAll()}}</div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "ES5Demo",
  data() {
    return {
      hello: "hello",
      obj1: {
        name: "Tom",
        age: "27"
      },
      obj2: {
        gender: "man",
        career: "teacher"
      }
    };
  },
  computed: {
    strTemplate() {
      return `${this.hello} template!`;
    },
    assignObj() {
      return Object.assign({}, this.obj1, this.obj2);
    }
  },
  methods: {
    getFuncDefaultValue(value = "I'm the default") {
      return value;
    },
    getNameAndAge() {
      const { name, age } = this.assignObj;
      return { name, age };
    },
    getNameAndCareer() {
      const { gender, age, ...other } = this.assignObj;
      return other;
    },
    getAll() {
      return { ...this.assignObj };
    }
  }
};
</script>

<style lang="scss" scoped>
</style>

