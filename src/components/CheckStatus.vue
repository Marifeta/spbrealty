<template>
  <div
      @click.stop="clickHandler"
      class="status"
  >
    <span
        class="status_text"
    >
      Все статусы
    </span>
    <div
        class="status_arrow"
        :class="{ status_arrow__rotate: isOpen }"
    ></div>
    <transition name="fade">
      <div
          v-if="isOpen"
          @click.stop="() => {}"
          class="status_field"
      >
        <Checkbox
            v-for="checkbox in checkboxes"
            :key="checkbox.id"
            :on-click="checkHandler"
            class="status_checkbox"
            :is-checked="checkbox.isChecked"
            :text="checkbox.text"
            :id="checkbox.id"
        />
      </div>
    </transition>
  </div>
</template>

<script>
import Checkbox from "./Checkbox";
export default {
  components: {Checkbox},
  props: {
    isOpen: {
      type: Boolean,
      required: true,
    },
    checkboxes: {
      type: Array,
      required: true,
    },
    checkHandler: {
      type: Function,
      required: true,
    },
    clickHandler: {
      type: Function,
      required: true,
    },
  },
}
</script>

<style lang="sass" scoped>
@import '../assets/main.sass'
.status
  cursor: pointer
  position: relative
  height: 38px
  display: flex
  flex-grow: 3
  align-items: center
  justify-content: space-between
  border: 1px solid $dark_border
  padding: 0 12px
  max-width: 174px
  white-space: nowrap
  min-width: 184px
  &_text
    @include middle_fonts
    line-height: 18px
  &_arrow
    background-image: url("../assets/arrow.svg")
    @include background_image
    height: 100%
    width: 10px
    margin-left: 6px
    transform: rotate(180deg)
    transition: transform 300ms ease
    &__rotate
      transform: rotate(360deg)
  &_field
    position: absolute
    z-index: 100
    width: 100%
    height: 124px
    background-color: $field
    box-shadow: 0 20px 25px -5px rgba(26, 32, 44, 0.1), 0px 10px 10px -5px rgba(26, 32, 44, 0.04)
    top: 0
    left: 0
    transform: translateY(44px)
  &_checkbox
    padding: 0 20px 15px
    &:first-child
      padding: 17px 20px 15px
.fade-enter-active, .fade-leave-active
  transition: opacity .5s
.fade-enter, .fade-leave-to
  opacity: 0
</style>
