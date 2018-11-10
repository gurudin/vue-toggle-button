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
          size="sm"
          @change="change"></toggle-button>
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
    
    <br>
    <div class="row">
      <div class="col-sm-1">
        select
      </div>
      <div class="col-sm-3">
        <select class="form-control" v-model="toggle.value">
          <option value="primary">Primary</option>
          <option value="secondary">Secondary</option>
          <option value="success">Success</option>
          <option value="danger">Danger</option>
          <option value="warning">Warning</option>
          <option value="info">Info</option>
          <option value="light">Light</option>
          <option value="dark">Dark</option>
        </select>
      </div>
    </div>
    <hr>
    
    <div class="row">
      <div class="col-sm-1">
        sm
      </div>
      <div class="col-sm">
        <toggle-button
          mode="checkbox"
          v-model="checkbox.value"
          :options="[]"
          :toggle='{checked: "warning", unchecked: "info"}'
          size="sm"></toggle-button>
      </div>
    </div>

    <br>
    <div class="row">
      <div class="col-sm-1">
        lg
      </div>
      <div class="col-sm">
        <toggle-button
          mode="checkbox"
          v-model="checkbox.value"
          :options="[]"
          :toggle='{checked: "danger", unchecked: "success"}'
          size="lg"></toggle-button>
      </div>
    </div>

    <br>
    <div class="row">
      <div class="col-sm-1">
        sm
      </div>
      <div class="col-sm">
        <toggle-button
          mode="checkbox"
          v-model="checkbox.value"
          :options='[{label: "On", value: 0}, {label: "Off", value: 1}]'
          size="sm"></toggle-button>
      </div>
    </div>

    <br>
    <div class="row">
      <div class="col-sm-1">
        lg
      </div>
      <div class="col-sm">
        <toggle-button
          mode="checkbox"
          v-model="checkbox.value"
          :options='checkbox.options'
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
        value: 'primary',
        options: [
          {label: "Primary", value: 'primary', checked: "primary"},
          {label: "Secondary", value: 'secondary', checked: "secondary"},
          {label: "Success", value: 'success', checked: "success"},
          {label: "Danger", value: 'danger', checked: "danger"},
          {label: "Warning", value: 'warning', checked: "warning"},
          {label: "Info", value: 'info', checked: "info"},
          {label: "Light", value: 'light', checked: "light"},
          {label: "Dark", value: 'dark', checked: "dark"},
        ],
      },
      checkbox: {
        value: 0,
        options: [
          {label: "Primary", value: 0},
          {label: "Secondary", value: 1},
        ]
      },
    };
  },
  methods: {
    change(value) {
      console.log(value);
      return true;
    }
  },
  components: {
    'toggle-button': ToggleButton
  }
}
</script>

<style>
@import "https://cdn.bootcss.com/twitter-bootstrap/4.1.3/css/bootstrap.min.css";
@import "https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css";
#app {
  margin-top: 20px;
}
</style>
