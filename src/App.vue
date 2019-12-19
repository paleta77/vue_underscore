<template>
  <div id="app">
    <MyTable>Movies</MyTable>
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
  width: 50%;
  margin: auto;
}
</style>
