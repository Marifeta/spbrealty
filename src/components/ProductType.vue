<template>
  <div class="type">
      <img
          v-if="type === 'Паркинг'"
          src="../assets/parking.svg"
          alt="parking icon"
          class="type_icon"
      >
      <img
          v-else src="../assets/apartment.svg"
          alt="apartment icon"
          class="type_icon"
      >
    <div class="type_text">
      {{ type.text }}
    </div>
    <Title
        class="type_title"
        :text="type.title"
    />
  </div>
</template>
<style lang="sass" scoped>
@import "../assets/main.sass"
.type
  cursor: pointer
  position: relative
  background: $type_color
  box-shadow: 0 0 2px rgba(94, 119, 157, 0.25)
  border-radius: 32px
  display: flex
  padding: 5px 16px 5px 17.4px
  align-items: center
  min-width: 20px
  &:hover
    .type_title
      visibility: visible
  &_text
    font-style: normal
    font-weight: normal
    font-size: 12px
    line-height: 16px
    @include ellipsis
    max-width: 108px
    user-select: none
  &_icon
    margin-right: 10px
  &_title
    visibility: hidden
    position: absolute
    top: 0
    left: 0
    transform: translate(33px, 41px)
@media (max-width: 1199px)
  .type
    &_title
      right: 0
      left: auto
</style>
<script>
import Title from "./Tooltip";
export default {
  components: {Title},
  props: {
    type: {
      type: Object,
      required: true,
    },
  },
  computed: {
  },
}
</script>
