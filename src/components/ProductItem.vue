<template>
    <article class="product">
        <img class="product__img" :src="product.img"/>
        <div class="product__inner">
        <strong class="product__name">{{product.title}}</strong>
        <p class="product__description">{{product.description}}</p>
        <strong class="product__price">{{product.price}} руб.</strong>
        </div>
        <div 
            @click="$emit('remove', product)" 
            class="product__remove">
            <img src="@/assets/icons/icon-remove.svg" alt="">
        </div>
    </article>
</template>

<script>
    export default {
        props: {
            product: {
                type: Object,
                required: true,
            }
        }
    }
</script>

<style lang="sass" scoped>
.product
    position: relative
    display: flex
    flex-direction: column
    justify-content: space-between
    min-height: 423px
    background: var(--color-secondary)
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02)
    border-radius: 4px
    cursor: pointer
    transition: 0.3s
    &__img
        width: 100%
        max-height: 200px
        height: auto
        object-fit: cover
    &__inner
        display: flex
        flex-direction: column
        padding: 0px 24px 16px 24px
        gap: 16px
    &__name
        font-size: var(--fs-xmedium)
        font-weight: var(--fw-semi-bold)
    &__description
        font-size: var(--fs-medium)
        font-weight: var(--fw-regular)
    &__price
        margin-top: 16px
        font-size: var(--fs-large)
        font-weight: var(--fw-semi-bold)
    &__remove
        cursor: pointer
        position: absolute
        right: -3%
        top: -2%
        display: none
    &:hover
        transform: scale(1.03)
        transition: 0.3s
        box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.3), 0px 6px 10px rgba(0, 0, 0, 0.3)
        .product__remove
            display: block


@media (max-width: 480px)
    .product
        min-height: auto
        gap: 10px
        &__inner
            padding: 10px 5
        .product__remove
            display: block
</style>