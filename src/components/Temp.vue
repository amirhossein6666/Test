<template>
  <div :class="{sale : theme === 'sale'}" class="color">
    <p>this text is from temp</p>
  </div>
  <button @click="closeTemp">close temp</button>
  <div>
    <slot name="links"></slot>
    <slot name="imagegi"></slot>
    <slot></slot>
  </div>
</template>
<script>
export default {
  props : ['theme'],
  methods : {
    closeTemp() {
      this.$emit('close')
    }
  }
}
</script>

<style>
.color.sale {
  color: red;
}
</style>


