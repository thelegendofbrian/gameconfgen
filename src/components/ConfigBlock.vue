<template>
  <div class="config-block">
    <h2>{{ config.configName }}</h2>
    <p>{{ config.configDesc }}</p>

    <template v-if="config.displayType === 0">
      <label>{{ config.options[sliderValue].name }}</label><br>
      <input type="range" min=0 :max="config.options.length-1" v-model="sliderValue" >
    </template>

    <template v-if="config.displayType === 1">
      <span v-for="item in config.options" :key="item.name">
        <input type="radio" :name="config.configName" :value="item.name" v-model="radioValue"/>
        <label>{{ item.name }}</label><br>
      </span>
    </template>

    <template v-if="config.displayType === 2">
      <input type="text" v-model="textValue" />
    </template>

    <template v-if="config.displayType === 3">
      <input type="checkbox" :id="config.configName" v-model="checkboxValue" />
    </template>

    <template v-if="config.displayType === 4">
      <select v-model="selectValue">
        <option v-for="item in config.options" :key="item.name" :value="item.name">
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
    if (this.config.displayType === 0) {
      return {sliderValue:this.config.defaultOption}
    } else if (this.config.displayType === 1) {
      return {radioValue:this.config.options[this.config.defaultOption].name}
    } else if (this.config.displayType === 2) {
      return {textValue:this.config.defaultOption}
    } else if (this.config.displayType === 3) {
      return {checkboxValue:this.config.options[this.config.defaultOption].name}
    } else if (this.config.displayType === 4) {
      return {selectValue:this.config.options[this.config.defaultOption].name}
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
