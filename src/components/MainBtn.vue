<template>
  <button
      class="btn"
  >
    <span class="btn_text">{{ text }}</span>
    <slot></slot>
  </button>
</template>
<script>
export default {
  props: {
    text: {
      type: String,
      required: true,
    },
  }
}
</script>
<style lang="sass" scoped>
@import '../assets/main.sass'
.btn
  display: flex
  align-items: center
  max-width: 154px
  height: 38px
  background-color: $main_btn
  padding: 0 12px 0 13px
  white-space: nowrap
  cursor: pointer
  &_text
    @include minimal_fonts
    line-height: 20px
    color: $main_text_color
    user-select: none
</style>
