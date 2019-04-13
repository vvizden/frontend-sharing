<template>
  <article :style="{fontSize: postFontSize + 'em'}">
    <h3 v-if="title">{{title}}</h3>
    <button v-defined-show="showButton" @click="$emit('enlarge-text',0.1)">Enlarge Text</button>
    <section>
      <slot></slot>
    </section>
  </article>
</template>

<script>
export default {
  name: "BlogPost",
  directives: {
    "defined-show": {
      inserted(el, binding) {
        if (binding.value === false) {
          el.style.display = "none";
        }
      }
    }
  },
  props: {
    title: {
      type: String
    },
    postFontSize: {
      type: Number,
      default: () => 1
    },
    showButton: {
      type: Boolean,
      default: () => true
    }
  }
};
</script>

<style>
</style>
