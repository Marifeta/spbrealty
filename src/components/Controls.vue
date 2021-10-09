<template>
  <div class="controls">
    <Checkbox
        :text="'все'"
        :is-checked="isChecked"
        class="controls_checkbox__margin"
        :on-click="clickHandler"
    />
    <MainBtn
        class="controls_btn__margin"
        :text="'Сохранить'"
    >
      <span class="controls_icon"></span>
    </MainBtn>
    <MainBtn
        :text="'Отправить'"
        class="controls_btn__margin"
    >
      <span class="controls_icon controls_icon__url"></span>
    </MainBtn>
    <MainBtn
        :text="'Удалить'"
        class="controls_btn__margin"
    >
      <span class="controls_icon controls_icon__url1"></span>
    </MainBtn>
  </div>
</template>

<script>
import MainBtn from "./MainBtn";
import Checkbox from "./Checkbox";

export default {
  components: {Checkbox, MainBtn},
  props: {
    clickHandler: {
      type: Function,
      required: true,
    },
    isChecked: {
      type: Boolean,
      required: true,
    }
  },
}
</script>

<style lang="sass" scoped>
@import "../assets/main.sass"
.controls
  display: flex
  &_btn__margin
    margin: 0 10px 0 0
  &_checkbox__margin
    margin: 0 13px 0 0
  &_icon
    background-image: url("../assets/pdf.svg")
    @include background_image
    height: 20px
    width: 20px
    min-height: 20px
    min-width: 20px
    margin-left: 12px
    &__url
      background-image: url("../assets/send.svg")
    &__url1
      background-image: url("../assets/remove.svg")
@media (max-width: 500px)
  .controls
    flex-direction: column
    &_checkbox__margin
      margin: 0 0 13px 0
    &_btn__margin
      margin: 0 0 10px 0
</style>
