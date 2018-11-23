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
- #### 样式设置
<img src="https://i.imgur.com/dfQGnBq.png" width="120">

```
<toggle-button :toggle='{checked: "info", unchecked: "dark"}'></toggle-button>
```

<img src="https://i.imgur.com/88UWf0C.png" width="120">

```
<toggle-button :toggle='{checked: "rgb(187, 153, 205)", unchecked: "rgb(191, 203, 217)"}'></toggle-button>
```

<img src="https://i.imgur.com/YU7xd09.png" width="140">

```
<toggle-button :options='[{label: "Offline", value: 0, "checked": "warning"}, {label: "Online", value: 1, "checked": "success"}]'></toggle-button>
```

- #### 是否可用
<img src="https://i.imgur.com/9Bt5uZe.png" width="120">

```
<toggle-button disabled></toggle-button>
```

## 复选框切换
- #### 尺寸
<img src="https://i.imgur.com/AB0VPxy.png" width="50">

```
<toggle-button mode="checkbox" :options='[]' size="sm"></toggle-button>
```

<img src="https://i.imgur.com/UphmlrF.png" width="70">

```
<toggle-button mode="checkbox" :options='[]'></toggle-button>
```

- #### 样式设置
<img src="https://i.imgur.com/7YSUYNH.png" width="70">

```
<toggle-button mode="checkbox" :toggle='{checked: "info", unchecked: "dark"}'></toggle-button>
```

<img src="https://i.imgur.com/WXggVpt.png" width="120">

```
<toggle-button mode="checkbox" :toggle='{checked: "rgb(187, 153, 205)", unchecked: "rgb(191, 203, 217)"}' :options='[{label: "Offline", value: 0}, {label: "Online", value: 1}]'></toggle-button>
```

- #### 是否可用

<img src="https://i.imgur.com/OMh176L.png" width="70">

```
<toggle-button mode="checkbox" disabled></toggle-button>
```

## 事件
- #### 改变前回调方法
```
HTML
<toggle-button
    v-model="value"
    mode="checkbox"
    size="sm"
    :options='options'
    :before="changeBefore"></toggle-button>

JS
const vm = new Vue({
    data() {
        return {
        value: false,
        options: [
            {label: "Active", value: false},
            {label: "Deactive", value: true}
        ]
        };
    },
    methods: {
        /**
        * 改变前回调
        *
        * @param obj.value 改变后值
        * @param obj.event 当前对象
        *
        * @return Boolean true=修改当前值  false=不修改当前值
        */
        changeBefore(obj) {
        var value = obj.value;
        var event = obj.event;
        
        if (confirm('改变后状态是' + value + ', 确认修改？')) {
            return true;
        } else {
            return false;
        }
        }
    }
});
```

- #### 改变回调方法
```
HTML
<toggle-button
    v-model="value"
    size="sm"
    :options='options'
    @change="change"></toggle-button>

JS
const vm = new Vue({
data() {
    return {
    value: false,
    options: [
        {label: "Deactive", value: false, checked: "warning"},
        {label: "Active", value: true, checked: "success"}
    ]
    };
},
methods: {
    change(obj) {
    var value = obj.value; // 改变后的值
    var event = obj.event; // 当前操作对象
    alert(value);
    }
}
});
```

## Props
```
/**
* 模式
*
* @type {String}
* 
* @required false
*
* `group` bootstrap `btn-group`样式
* `checkbox` 复选框样式
*/
mode: {
    type: String,
    required: false,
    default: 'group' // group|checkbox
},
/**
* 绑定数据
*
* @type {mixed}
*
* @required true
*/
value: {
    type: null,
    required: true,
    default: 0
},
/**
* 回传数据 (透传数据)
*
* @type {mixed}
*
* @required false
*/
data: {
    type: null,
    required: false,
    default: ''
},
/**
* 选择数据
*
* @type {Array}
* 
* @required true
*
* @example [
*     {label: "Left", value: 1, checked: "primary"},
*     {label: "Middle", value: 2, checked: "info"},
*     {label: "Right", value: 3}
* ]
* label: 标签描述
* value: 标签值
* checked: 选中样式
*/
options: {
    type: Array,
    required: true
},
/**
* 样式设置
* 
* @type {Object}
* 
* @required false
* 
* @example {checked: "success", unchecked: "secondary"}
* checked: 选中样式
* unchecked: 未选中样式
* 
* bootstrap3 default|primary|success|info|warning|danger
* bootstrap4 primary|secondary|success|danger|warning|info|light|dark
*
* 自定义颜色 rgb(187, 153, 205)|red|#000000
*/
toggle: {
    type: Object,
    required: false,
    default: () =>{
        return { checked: "success", unchecked: "secondary" };
    } 
},
/**
* 尺寸
* 
* @type {String}
* 
* @required false
* 
* @example ''|sm|lg
*/
size: {
    type: String,
    required: false,
    default: ''
},
/**
* 是否可用
* 
* @type {Boolean}
* 
* @required false
* 
* @example true|false
*/
disabled: {
    type: Boolean,
    required: false,
    default: false
},
/**
* 改变前回调方法
*
* @type {Function}
*
* @required false
*
* @param value 改变后值
* @param event 当前对象
*/
before: {
    type: Function,
    required: false,
}
```