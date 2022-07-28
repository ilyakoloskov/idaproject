<template>
  <section class="products__wrap" v-if="products.length > 0">
    <transition-group name="products-list">
      <product-item
        :product="product"
        v-for="product in products"
        :key="product.id"
        @remove="$emit('remove', product)"
      >
      </product-item>
    </transition-group>
  </section>
  <section class="products__none" v-else>
    <h3 class="products__none-title">Список товаров пуст</h3>
    <my-button @click="$emit('showDialog')" class="products__btn btn_active"
      >Добавить товар</my-button
    >
  </section>
</template>

<script>
import ProductItem from "@/components/ProductItem.vue";
import MyButton from "./UI/MyButton.vue";
export default {
  components: {
    ProductItem,
    MyButton,
  },
  props: {
    products: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="sass" scoped>
.products
    &__wrap
        display: grid
        grid-template-columns: repeat(auto-fill, minmax(332px, 1fr))
        gap: 16px
        margin-top: 16px
    &__none
        display: grid
        place-content: center
        height: 100%
        &-title
            font-size: var(--fs-xlarge)

.products-list-item
    display: inline-block

.products-list-enter-active,
.products-list-leave-active
    transition: 0.5s

.products-list-enter-active
    transition: 1s
    transform: translateY(-80px)
    opacity: 0
.products-list-enter-to
    transition: 0.3s
    transform: translateY(0px)
    opacity: 1
.products-list-leave-to
    opacity: 0
    transform: translateY(30px)


@media (max-width: 480px)
    .products__wrap
        grid-template-columns: repeat(auto-fill, minmax(100%, 1fr))
        gap: 30px
</style>
