<template>
  <div class="input">
    <div class="input_loupe"></div>
    <input
        @input="setInput($event)"
        :value="keyword"
        class="input_enter"
        placeholder="Введите ЖК / корпус / № квартиры / № паркинга"
        type="search"
    >
  </div>
</template>

<style lang="sass" scoped>
@import '../assets/main.sass'
.input
  display: flex
  height: 38px
  border: 1px solid $dark_border
  width: 637px
  min-width: 200px
  &_loupe
    height: 100%
    width: 38px
    background-image: url("../assets/search.svg")
    @include background_image
  &_enter
    height: 100%
    width: 100%
    background-color: inherit
</style>

<script>
export default {
  props: {
    keyword: {
      type: String,
      required: true,
    },
    setInput: {
      type: Function,
      required: true,
    },
  },
}
</script>
