<template>
  <div class="config-block">
    <h2>{{ config.configName }}</h2>
    <p>{{ config.configDesc }}</p>

    <template v-if="config.displayType === 0">
      <label>{{ config.options[sliderValue].name }}</label>
      <input type="range" min=0 :max="config.options.length-1" v-model="sliderValue" >
    </template>

    <template v-if="config.displayType === 1">
      <span v-for="item in config.options" :key="item.name">
        <input type="radio" name="radio" value="item.name"/>
        <label>{{ item.name }}</label><br>
      </span>
    </template>

    <template v-if="config.displayType === 2">
      <input type="text" />
    </template>

    <template v-if="config.displayType === 3">
      <input type="checkbox" />
    </template>

    <template v-if="config.displayType === 4">
      <select>
        <option v-for="item in config.options" :key="item.name" value="">
          {{ item.name }}
        </option>
      </select>
    </template>

  </div>
</template>

<script>
export default {
  name: 'YOLO',
  props: {
    config: Object
  },
  data: function() {
    return {
      sliderValue:2
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
