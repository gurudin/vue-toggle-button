<template>
  <span>
    <div
      class="btn-group"
      :class="size!='' ? 'btn-group-' + size : ''"
      role="group"
      v-if="mode=='group'">

      <button
        :disabled="disabled"
        type="button"
        class="btn"
        v-for="opt in options"
        :class="toggleClass(opt)"
        @click="toggleButton(opt)">{{opt.label}}</button>
    </div>

    <div
      class="gurudin-toggle-switch gurudin-switch-lg"
      :class="switchClass()"
      v-if="mode == 'checkbox'"
      @click="toggleSwitch"></div>

    <input type="hidden" :value="value">
  </span>
</template>

<script>
export default {
  name: "ToggleButton",
  props: {
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
    }
  },
  data() {
    return {
      toggleClass(opt) {
        if (opt.checked === undefined) {
          return this.value === opt.value ? 'btn-' + this.toggle.checked : 'btn-' + this.toggle.unchecked;
        } else {
          return this.value === opt.value ? 'btn-' + opt.checked : 'btn-' + this.toggle.unchecked;
        }
      },
      switchClass() {
        var retClass = ' gurudin-switch-' + this.size;

        if (this.value == 1 || this.value == true) {
          // retClass += ' gurudin-checked bg-' + this.toggle.checked;
          retClass += ' bg-' + this.toggle.checked;
        } else {
          retClass += ' bg-' + this.toggle.unchecked;
        }
        
        return retClass;
      }
    };
  },
  computed: { },
  methods: {
    setValue(value) {
      this.$emit('input', value);
    },
    toggleButton(opt) {
      if (this.value == opt.value) {
        return false;
      }

      this.setValue(opt.value);
    },
    toggleSwitch(event) {
      if (this.options.length == 0) {
        this.setValue(!this.value);
      }

      console.log(window.getComputedStyle(event.target, '::before').getPropertyValue('transform'));
      window.getComputedStyle(event.target, '::before').setProperty('transform', 'matrix(1, 0, 0, 1, 45, 3)')
    }
  },
}
</script>

<style>
.gurudin-toggle-switch {
  /* background-color: rgb(191, 203, 217); */
  border-radius: 999px;
  display: inline-block;
  position: relative;
  outline: 0;
  box-sizing: border-box;
  cursor: pointer;
}
.gurudin-toggle-switch::before {
  display: block;
  position: absolute;
  overflow: hidden;
  top: 0;
  left: 0;
  z-index: 20;
  transform: translate(3px,3px);
  transition: transform .3s;
  border-radius: 100%;
  background-color: #fff;
  content: "";
}
.gurudin-checked::before {
  transform: translate(45px,3px);
}

.gurudin-switch-lg {
  min-width: 80px;
  min-height: 38px;
}
.gurudin-switch-lg::before {
  width: 32px;
  height: 32px;
}

.gurudin-switch-sm {
  min-width: 50px;
  min-height: 22px;
}
.gurudin-switch-sm::before {
  width: 16px;
  height: 16px;
}

</style>

