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
    mode: {
      type: String,
      required: false,
      default: 'group' // group|checkbox
    },
    value: {
      type: null,
      required: true,
    },
    options: {
      type: Array,
      required: true
    },
    toggle: {
      type: Object,
      required: false,
      default: () =>{
        return { checked: "success", unchecked: "secondary" };
      } 
    },
    size: {
      type: String,
      required: false,
      default: ''
    },
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
.fade-enter,.fade-leave-to{opacity:0;}
.fade-enter-active,.fade-leave-active{transition:opacity .5s;}
</style>

