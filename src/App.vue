<template>
  <div id="app">
    <h1>Don't Starve Together Config Generator</h1>
    <ConfigBlock
      v-for="item in spoofData"
      :key="item.configName"
      :config='item'
    />
  </div>
</template>

<script>
import ConfigBlock from './components/ConfigBlock.vue'
import Sample from './sample.json'

export default {
  name: 'App',
  data: function () {
    return {
      spoofData: Sample
    }
  },
  components: {
    ConfigBlock
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 10px;
}
</style>
