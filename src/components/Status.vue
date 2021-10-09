<template>
  <div
      class="status"
      :style="getColor"
  >
    <div class="status_point" :style="{backgroundColor: getColor.color}"></div>
    <div class="status_text">{{ status.text }}</div>
  </div>
</template>

<style lang="sass" scoped>
@import "../assets/main.sass"
.status
  height: 30px
  padding: 0 9px
  display: flex
  align-items: center
  &_point
    width: 6px
    height: 6px
    border-radius: 50%
    margin-right: 8px
  &_text
    @include middle_fonts
    line-height: 18px
    white-space: nowrap
    user-select: none
</style>

<script>
export default {
  props: {
    status: {
      type: Object,
      required: true,
    },
  },
  computed: {
    getColor() {
      if (this.status.type === 'entity') return {backgroundColor: '#FFE4E4', color: '#DD4C5D'};
      if (this.status.type === 'individual') return {backgroundColor: '#D6F5FF', color: '#0291C1'};
      if (this.status.type === 'booked') return {backgroundColor: '#EDEDED', color: '#686868'};
      if (this.status.type === 'sold') return {backgroundColor: '#CCCCCC', color: '#808080'};
      return {display: 'none'}
    },
  },
}
</script>
