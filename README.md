# [docs for vue-toggle-button](https://gurudin.github.io/vue-toggle-button/) [![NPM version](https://img.shields.io/npm/v/vue-toggle-button.svg)](https://www.npmjs.com/package/vue-toggle-button)

> VueJs for toggle button

## 安装 (Installation)
- #### 添加包:

``` bash
$ yarn add vue-toggle-button
```
``` bash
$ npm install vue-toggle-button
```

- #### 引入模块
```
import ToggleButton from "vue-toggle-button";
```

- #### 文件引入
```
<!-- CDNJS :: Vue (https://cdnjs.com/) -->
<script src="//cdnjs.cloudflare.com/ajax/libs/vue/2.5.2/vue.min.js"></script>

<!-- Require js -->
<script src="//vue-toggle-button.min.js"></script>
```

- #### 示例
<img src="https://i.imgur.com/h0bCTYT.png" width="160">

```base
# HTML
<toggle-button
  mode="checkbox"
  v-model="value"
  :options='options'></toggle-button>

# JS
Vue.component('toggle-button', VueToggleButton.toggleButton)
const vm = new Vue({
  el: "#app",
  data() {
    return {
      options: [
        {label: "Active", value: 'active'},
        {label: "Deactive", value: 'deactive'}
      ]
      value: 'active'
    };
  }
});
```

## 按钮切换
- #### 尺寸
<img src="https://imgur.com/I5dr3iD.png" width="100">

```
<toggle-button size="sm"></toggle-button>
```

<img src="https://imgur.com/OcZZjuf.png" width="120">

```
<toggle-button size=""></toggle-button>
```

<img src="https://i.imgur.com/6fKzPAX.png" width="150">

```
<toggle-button :toggle='{checked: "info", unchecked: "dark"}'></toggle-button>
```