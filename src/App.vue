<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<!-- use the ExcelReader component in your main App.vue file 
  to display the file upload and data reading functionality. -->
<template>
  <div id="app">
    <h1>Vite + Vue + Excel Reader</h1>
    <ExcelReader />
  </div>
</template>

<script>
import ExcelReader from './components/ExcelReader.vue';

export default {
  name: 'App',
  components: {
    ExcelReader
  }
};
</script>

<style>
#app {
  text-align: center;
  margin-top: 50px;
}
</style>
