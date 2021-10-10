<template>
  <div
      @click.stop="closeFilters"
      class="list"
  >
    <div class="list_wrapper">
      <Search
          :value="keyword"
          :on-input="onInputChange"
          :filters="filters"
          :is-open="isOpenFilters"
          :open-filters="openFilters"
          :set-filter="setFilter"
          class="list_search"
      />
      <Controls
          :is-checked="getCheckedAll"
          :click-handler="checkAllProducts"
          class="list_controls"
      />
      <div class="list_prod" v-if="filteredProducts.length">
        <Product
            v-for="product of filteredProducts"
            :key="product.id"
            :item="product"
            class="list_item"
            :click-handler="checkProduct"
        />
      </div>
    </div>
  </div>
</template>

<style lang="sass" scoped>
.list
  &_wrapper
    max-width: 1200px
    margin: 0 auto
    height: 100%
    padding: 89px 100px 61px 99px
  &_search
    margin-bottom: 32px
  &_controls
    margin-bottom: 20px
  &_prod
    display: flex
    flex-flow: row wrap
    justify-content: center
  &_item
    margin: 0 0 23px 0
    &:nth-of-type(2n)
      margin: 0 0 23px 23px
@media (max-width: 820px)
  .list_wrapper
    padding: 49px 24px 61px 24px
@media (max-width: 669px)
  .list_item
      &:nth-of-type(2n)
        margin: 0 0 23px 0
</style>

<script>
import Search from "../components/Search";
import Product from "../components/Product";
import Controls from "../components/Controls";

export default {
  components: {
    Controls,
    Search,
    Product,
  },
  data() {
    return {
      keyword: '',
      products: [
        {
          id: '1',
          isLiving: true,
          price: '7 733 300',
          type: {
            text: 'Квартира',
            title: 'Апартаменты',
          },
          name: 'Чистое Небо',
          info: 'корпус 10, III кв. 2022 г.',
          location: 'Лен. область, Всеволожский район, д. Кудрово, ул. Столичная, д. 5, к. 1',
          added: 'Добавлено 21/11/2020',
          status: {
            type: 'entity',
            text: 'Уступка от юр. лица',
          },
          params: ['кв. 62', '234.38 м²', '1 комн. кв.',  '7 этаж',],
          isChecked: false,
        },
        {
          id: '2',
          isLiving: true,
          price: '7 733 300',
          type: {
            text: 'Квартира',
            title: 'Апартаменты',
          },
          name: 'Зеленый квартал на Пулковских высотах',
          info: 'корпус 9, III кв. 2022 г.',
          location: 'Лен. область, Всеволожский район, д. Кудрово, ул. Столичная, д. 5, к. 1',
          added: 'Добавлено 21/11/2020',
          params: ['кв. 62', '234.38 м²', '1 комн. кв.',  '7 этаж',],
          status: {
            type: 'individual',
            text: 'Уступка от физ. лица',
          },
          isChecked: false,
        },
        {
          id: '3',
          isLiving: true,
          price: '800 300',
          type: {
            text: 'Паркинг',
            title: 'Наземная, открытая',
          },
          name: 'Зеленый квартал на Пулковских высотах',
          info: 'корпус 8, III кв. 2022 г.',
          location: 'Лен. область, Всеволожский район, д. Кудрово, ул. Столичная, д. 5, к. 1',
          added: 'Добавлено 21/11/2020',
          params: ['№ 7-10-2 (ПИБ №68)', '15 м²',],
          status: {
            type: 'booked',
            text: 'Забронировано',
          },
          isChecked: false,
        },
        {
          id: '4',
          isLiving: true,
          price: '7 733 300',
          type: {
            text: 'Паркинг',
            title: 'Подземная встроенно-пристроенная',
          },
          name: 'Зеленый квартал на Пулковских высотах',
          info: 'корпус 8, III кв. 2022 г.',
          location: 'Лен. область, Всеволожский район, д. Кудрово, ул. Столичная, д. 5, к. 1',
          added: 'Добавлено 21/11/2020',
          params: ['№ 7-10-2 (ПИБ №68)', '16 м²',],
          status: {
            type: 'sold',
            text: 'Продано',
          },
          isChecked: false,
        },
      ],
      filteredProducts: [],
      isOpenFilters: false,
      filters: [
        {
          id: '1',
          isChecked: true,
          text: 'Забронировано',
          type: 'booked'
        },
        {
          id: '2',
          isChecked: true,
          text: 'Продано',
          type: 'sold',
        },
        {
          id: '3',
          isChecked: true,
          text: 'Активно',
          type: 'active'
        },
      ],
    };
  },
  computed: {
    getCheckedAll() {
      return Boolean(this.filteredProducts.every((product) => (product.isChecked)) && this.filteredProducts.length);
    },
  },
  created() {
    this.filteredProducts = [...this.products];
  },
  methods: {
    onInputChange(e) {
      this.keyword = e.target.value.trim();
      this.filteredProducts = this.products.filter((i) => {
        if (i.name.toLowerCase().indexOf(this.keyword.toLowerCase()) > -1
            || i.info.toLowerCase().indexOf(this.keyword.toLowerCase()) > -1
        ) {
          return i
        }
      });
    },
    closeFilters() {
      this.isOpenFilters = false;
    },
    openFilters() {
      this.isOpenFilters = !this.isOpenFilters;
    },
    filterProducts() {
      const activeFilter = this.filters.filter((filter) => (filter.isChecked));
      this.filteredProducts = this.products.filter((product) => {
        for (let i = 0; i < activeFilter.length; i += 1) {
          if (product.status.type === activeFilter[i].type) {
            return product;
          } else if ((product.status.type === 'individual' || product.status.type === 'entity')
              && activeFilter[i].type === 'active') {
            return product;
          }
        }
      });
    },
    setFilter(id) {
      this.filters = this.filters.map((box) => {
        if (box.id === id) {
          return {...box, isChecked: !box.isChecked}
        }
        return box
      });
      this.filterProducts();
    },
    checkAllProducts() {
      this.filteredProducts = this.filteredProducts.map((product) => {
        if (this.getCheckedAll) {
          return {
            ...product,
            isChecked: false,
          }
        } else {
          return {
            ...product,
            isChecked: true,
          }
        }
      });
    },
    checkProduct(id) {
      this.filteredProducts = this.filteredProducts.map((product) => {
        if (product.id === id) {
          return {
            ...product,
            isChecked: !product.isChecked,
          }
        }
        return product;
      });
    },
  },

}
</script>
