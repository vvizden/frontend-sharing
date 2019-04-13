<template>
  <div id="app">
    <!-- <img src="./assets/logo.png">
    <div>
      <p>
        If Element is successfully added to this project, you'll see an
        <code v-text="'<el-button>'"></code>
        below
      </p>
      <el-button>el-button</el-button>
    </div>
    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <BoxSizingDemo/>
    <HrLine/>
    <FlexDemo/>
    <HrLine/>
    <ESDemo/>
    <HrLine/>
    <VueBindingDemo/>
    <HrLine/>
    <EventDemo/>
    <HrLine/>
    <KeyBindingDemo/>
    <HrLine/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import HrLine from "./components/HrLine.jsx";
import BoxSizingDemo from "./views/BoxSizingDemo.vue";
import FlexDemo from "./views/FlexDemo.vue";
import ESDemo from "./views/ESDemo.vue";
import VueBindingDemo from "./views/VueBindingDemo.vue";
import KeyBindingDemo from "./views/KeyBindingDemo.vue";
import EventDemo from "./views/EventDemo.vue";

export default {
  name: "app",
  components: {
    // HelloWorld,
    BoxSizingDemo,
    HrLine,
    FlexDemo,
    ESDemo,
    VueBindingDemo,
    KeyBindingDemo,
    EventDemo
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  /* margin-top: 60px; */
}

::-webkit-scrollbar {
  width: 7px;
  height: 7px;
  background-color: #ffffff;
}

::-webkit-scrollbar-thumb {
  border-radius: 5px;
  background-color: rgba(144, 146, 152, 0.3);
}

::-webkit-scrollbar-track-piece {
  background-color: #fff;
}
</style>
