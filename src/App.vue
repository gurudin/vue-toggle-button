<template>
  <div class="container-fluid" id="app">
    <div class="row">
      <div class="col-sm-1">
        sm
      </div>
      <div class="col-sm">
        <toggle-button
          v-model="toggle.value"
          :options="toggle.options"
          size="sm"></toggle-button>
      </div>
    </div>
    
    <br>
    <div class="row">
      <div class="col-sm-1">
        default
      </div>
      <div class="col-sm">
        <toggle-button
          v-model="toggle.value"
          :options="toggle.options" size=""></toggle-button>
      </div>
    </div>

    <br>
    <div class="row">
      <div class="col-sm-1">
        lg
      </div>
      <div class="col-sm">
        <toggle-button
          v-model="toggle.value"
          :options="toggle.options"
          size="lg"
          disabled></toggle-button>
      </div>
    </div>
    
  </div>
</template>

<script>
import ToggleButton from "./ToggleButton"

export default {
  name: 'App',
  data() {
    return {
      toggle: {
        value: '',
        options: [
          {label: "Left", value: 1, checked: "primary"},
          {label: "Middle", value: 2, checked: "info"},
          {label: "Right", value: 3}
        ],
      },
    };
  },
  components: {
    ToggleButton
  }
}
</script>

<style>
#app {
  margin-top: 20px;
}
</style>
