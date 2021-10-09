<template>
  <div class="card">
    <div class="card_checkbox">
      <Checkbox
          :on-click="clickHandler"
          :id="item.id"
          :is-checked="item.isChecked"
      />
    </div>
    <div class="card_article">
      <div class="card_wrapper">
        <div>
          <div class="card_main">
            <div
                class="card_price"
            >
              {{ item.price }} руб.
            </div>
            <ProductType :type="item.type"/>
          </div>
          <div>
            <div class="card_name">
              {{ item.name }},&nbsp;
              <span class="card_name__color">
                {{ item.info }}
              </span>
            </div>
          </div>
        </div>
        <Param
            class="card_param"
            :params="item.params"
        />
        <div class="card_locale">
          <div class="card_icon">
          </div>
          <div class="card_location">
            {{ item.location }}
          </div>
        </div>
      </div>
      <div class="card_resize">
        <Status
            :status="item.status"
            class="card_status__margin"
        />
        <div class="card_img">
          <img src="../assets/product.png" alt="icon">
          <div class="card_add">
            {{ item.added }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style lang="sass" scoped>
@import '../assets/main.sass'
.card
  display: flex
  padding: 25px 0 25px 25px
  border: 1px solid $light_border
  background-color: white
  flex: 1
  max-width: 489px
  min-width: 390px
  &_checkbox
    display: flex
    align-items: center
    margin-right: 25px
  &_article
    display: flex
    flex: 1
    min-width: 0
  &_wrapper
    display: flex
    flex-direction: column
    justify-content: space-between
    margin-right: 32px
    min-width: 0
  &_main
    display: flex
    align-items: center
    margin-bottom: 6px
  &_price
    display: inline-block
    white-space: nowrap
    @include large_fonts
    line-height: 20px
    color: $price
    margin-right: 16px
  &_name
    display: inline-block
    @include middle_fonts
    line-height: 150%
    color: $main_text_color
    margin-bottom: 10px
    &__color
      color: $secondary_text_color
  &_param
    margin-bottom: 10px
  &_locale
    position: relative
  &_icon
    background-image: url("../assets/locale.svg")
    @include background_image
    height: 13px
    width: 9px
    position: absolute
    left: 0
    transform: translate(-16px, 3px)
  &_location
    @include middle_fonts
    line-height: 150%
  &_add
    @include minimal_fonts
    line-height: 20px
    color: $secondary_text_color
    white-space: nowrap
    margin-right: 25px
  &_status__margin
    margin-bottom: 27.81px

@media (max-width: 1199px)
  .card
    padding: 16px 0 16px 16px
    &_article
      flex-wrap: wrap-reverse
    &_checkbox
      margin-right: 16px
    &_resize
      display: flex
      flex-direction: row-reverse
      flex-wrap: wrap
      width: 100%
      justify-content: space-between
    &_add
      margin-bottom: 10px
    &_img
      flex-grow: 1
    &_wrapper
      margin-right: 32px
@media (max-width: 1020px)
  .card
    min-width: 290px
@media (max-width: 669px)
   .card
     min-width: 100%
     &_resize
       display: block
       width: auto
     &_img
       flex-grow: 0
     &_add
       margin-bottom: 0
     &_article
       flex-wrap: nowrap

@media (max-width: 549px)
  .card
    min-width: 290px
    &_article
      flex-wrap: wrap-reverse
    &_add
      margin-bottom: 10px
    &_resize
      display: flex
      flex-direction: row-reverse
      flex-wrap: wrap
      width: 100%
      justify-content: space-between
    &_img
      flex-grow: 1
</style>
<script>
import ProductType from "./ProductType";
import Status from "./Status";
import Checkbox from "./Checkbox";
import Param from './Param';

export default {
  components: {Checkbox, Status, ProductType, Param},
  props: {
    item: {
      type: Object,
      required: true,
    },
    clickHandler: {
      type: Function,
      required: true,
    },
  },
}
</script>
