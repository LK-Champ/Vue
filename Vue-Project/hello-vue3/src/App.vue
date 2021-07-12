<template>
  <div v-for="item in list" :ref="setItemRef" :key="item">
    <div>1</div>
  </div>
</template>

<script>
import { onBeforeUpdate, onUpdated } from "vue";

export default {
  name: 'App',
  data() {
    return {
      list: [1,2,3,4]
    }
  },
  setup() {
    let itemRefs = [];

    const setItemRef = el => {
      itemRefs.push(el);
    }

    onBeforeUpdate(() => {
      itemRefs = []
    });

    onUpdated(() => {
      console.log(itemRefs)
    });

    return {
      itemRefs,
      setItemRef
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
