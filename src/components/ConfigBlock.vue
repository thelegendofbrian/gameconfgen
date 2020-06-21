<template>
  <div class="config-block">
    <h3>{{ config.configName }}</h3>
    <p>{{ config.configDesc }}</p>

    <template v-if="config.displayType === 0">
      <label class="slider">{{ config.options[sliderValue].name }}</label><br>
      <input type="range" class="slider" min=0 :max="config.options.length-1" :name="config.configId" v-model="sliderValue" >
    </template>

    <template v-if="config.displayType === 1">
      <span v-for="item in config.options" :key="item.name">
        <input type="radio" :name="config.configId" :value="item.id" v-model="radioValue"/>
        <label>{{ item.name }}</label><br>
      </span>
    </template>

    <template v-if="config.displayType === 2">
      <input type="text" :name="config.configId" v-model="textValue" />
    </template>

    <template v-if="config.displayType === 3">
      <input type="checkbox" :name="config.configId" :id="config.configId" v-model="checkboxValue" />
    </template>

    <template v-if="config.displayType === 4">
      <select :name="config.configId" v-model="selectValue">
        <option v-for="item in config.options" :key="item.id" :value="item.id">
          {{ item.name }}
        </option>
      </select>
    </template>

  </div>
</template>

<script>
export default {
  props: {
    config: Object
  },
  data: function() {
    if (this.config.displayType === 0) {
      return {sliderValue:this.config.defaultOption}
    } else if (this.config.displayType === 1) {
      return {radioValue:this.config.options[this.config.defaultOption].id}
    } else if (this.config.displayType === 2) {
      return {textValue:this.config.defaultOption}
    } else if (this.config.displayType === 3) {
      return {checkboxValue:this.config.options[this.config.defaultOption].id}
    } else if (this.config.displayType === 4) {
      return {selectValue:this.config.options[this.config.defaultOption].id}
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .config-block {
    display: inline-block;
    vertical-align: top;
    padding: 0 15px 0 15px;
    margin-bottom: 15px;
    width: 250px;
  }
  .config-block h3 {
    margin-top: 0;
  }
  input.slider {
    width: 90%;
  }
</style>
