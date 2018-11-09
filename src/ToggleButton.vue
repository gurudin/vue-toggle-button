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
      }
    };
  },
  computed: {
    
  },
  methods: {
    toggleButton(opt) {
      if (this.value == opt.value) {
        return false;
      }

      this.$emit('input', opt.value);
    }
  },
}
</script>

<style>
/* .fade-enter,.fade-leave-to{opacity:0;}
.fade-enter-active,.fade-leave-active{transition:opacity .5s;} */
</style>

