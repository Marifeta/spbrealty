<template>
  <div
      v-if="params && params.length"
      class="param"
  >
    <div class="param_group">
      <div
          v-for="(param, idx) of getFirstParams"
          :key="`${idx}_first`"
          class="param_text"
      >
        {{ param }}
      </div>
    </div>
    <div
        class="param_divider"
    ></div>
    <div class="param_group">
      <div
          v-for="(param, idx) of getSecondParams"
          :key="`${idx}_second`"
          class="param_text"
      >
        {{ param }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    params: {
      type: Array,
      required: false,
    },
  },
  computed: {
    getFirstParams() {
      return this.params.filter((param, idx) => (idx % 2 === 0))
    },
    getSecondParams() {
      return this.params.filter((param, idx) => (idx % 2 !== 0))
    },
  },
}
</script>
<style lang="sass" scoped>
@import "../assets/main.sass"
.param
  display: flex
  &_divider
    border-left: 1px solid $dark_border
    height: 100%
    width: 1px
    min-width: 0
    margin: 0 20px
  &_group
    display: flex
    flex-direction: column
    @include ellipsis
    min-width: auto
  &_text
    @include ellipsis
    display: block
    @include middle_fonts
    line-height: 25px
</style>
