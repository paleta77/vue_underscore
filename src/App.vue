<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <MyTable></MyTable>
  </div>
</template>

<script>
import MyTable from "@/components/MyTable";

export default {
  name: 'app',
  components: {
    MyTable
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
