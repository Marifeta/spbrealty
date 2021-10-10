<template>
  <div class="search">
    <SearchInput :value="value" :on-input="onInput" class="search_input search__top search__margin" />
    <CheckStatus
        :is-open="isOpen"
        :click-handler="openFilters"
        :check-handler="setFilter"
        :checkboxes="filters"
        class="search_status search__top search__margin"
    />
    <MainBtn class="search__top" :text="'Очистить корзину'" >
      <span class="search_icon"></span>
    </MainBtn>
  </div>
</template>

<style lang="sass" scoped>
@import '../assets/main.sass'
.search
  display: flex
  flex-wrap: wrap
  width: 100%
  &_input
    flex-grow: 1
  &_status
    flex-grow: 3
  &__top
    margin-top: 10px !important
  &__margin
    margin: 0 10px 0 0
  &_icon
    background-image: url("../assets/x.svg")
    height: 12px
    width: 12px
    margin-left: 12px
    @include background_image
@media (max-width: 1200px)
  .search__margin:first-child
    margin: 0
  .search_input
    width: 100%
@media (max-width: 1048px)
  .search_input
    width: 100%

</style>

<script>
import SearchInput from "./SearchInput";
import MainBtn from "./MainBtn";
import CheckStatus from "./CheckStatus";
export default {
  components: {
    CheckStatus,
    MainBtn,
    SearchInput,
  },
  props: {
    value: {
      type: String,
      required: true,
    },
    filters: {
      type: Array,
      required: true,
    },
    isOpen: {
      type: Boolean,
      required: true,
    },
    setFilter: {
      type: Function,
      required: true,
    },
    openFilters: {
      type: Function,
      required: true,
    },
    onInput: {
      type: Function,
      required: true,
    },
  },
};
</script>
