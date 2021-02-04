<template>
  <div id="app">
    <DragDrop />
  </div>
</template>

<script>
import DragDrop from './components/DragDrop.vue';

export default {
  name: 'App',
  components: {
    DragDrop
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
