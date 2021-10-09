<template>
  <label
      class="container"
  >
    <span
        v-if="isChecked"
        class="checkbox checkbox_check"
    >
      <img src="../assets/check.svg" alt="checked">
    </span>
    <span
        v-else
        class="checkbox"
    >
    </span>
    <span
        v-if="text && text.length"
        class="checkbox_text"
    >
      {{ text }}
    </span>
  <input
      v-show="false"
      :checked="isChecked"
      class="checkbox-input"
      @click.stop="onClick(id)"
  >
  </label>

</template>

<style lang="sass" scoped>
@import "../assets/main.sass"
.container
  display: flex
  align-items: center
  cursor: pointer
.checkbox
  height: 16px
  width: 16px
  display: flex
  justify-content: center
  align-items: center
  border: 1px solid $dark_border
  user-select: none
  &_check
    background: $checked
  &_text
    margin-left: 15px
    user-select: none
    @include minimal_fonts
</style>
<script>
export default {
  props: {
    isChecked: {
      required: true,
      type: Boolean,
    },
    text: {
      type: String,
      required: false,
    },
    id: {
      type: String,
      required: false,
    },
    onClick: {
      type: Function,
      required: false,
    }
  }
}
</script>
