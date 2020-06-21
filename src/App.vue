<template>
  <div id="app">
    <h1>Don't Starve Together Config Generator</h1>
    <hr>
    <form action="/getconfig" method="get">
      <template v-for="entry in spoofData">
        <h2 :key="entry.category">{{ entry.category }}</h2>
        <ConfigBlock
          v-for="item in entry.contents"
          :key="item.configId"
          :config='item'
        />
      </template>
      <hr>
      <button type="submit">Generate config</button>
    </form>
  </div>
</template>

<script>
import ConfigBlock from './components/ConfigBlock.vue'
import Sample from './sample.json'

export default {
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
  margin-left: 15px;
}
button {
  font-size: 1.2em;
}
</style>
