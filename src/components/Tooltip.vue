<template>
  <div class="tooltip">{{ text }}</div>
</template>
<style lang="sass" scoped>
@import "../assets/main.sass"
.tooltip
  height: 44px
  box-shadow: 0 8px 30px -3px rgba(26, 32, 44, 0.1), 0px 4px 6px -2px rgba(26, 32, 44, 0.05)
  background: $tooltip_bg
  padding: 20px
  position: relative
  color: $tooltip_text
  max-width: 300px
  display: flex
  align-items: center
  white-space: nowrap
  @include minimal_fonts
  line-height: 155%
  font-feature-settings: 'zero' on
  &::after
    content: ''
    position: absolute
    left: 0
    top: 0
    transform: translate(10px, -20px)
    border: 10px solid transparent
    border-bottom: 10px solid rgba(0, 0, 0, 0.5)
@media (max-width: 1199px)
  .tooltip
    &::after
      right: 0
      left: auto
      transform: translate(-68px, -20px)
</style>
<script>
export default {
  props: {
    text: {
      type: String,
      required: true,
    },
  },
}
</script>
