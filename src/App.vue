<template>
  <main class="main">
    <!-- PRODUCT-FORM -->
    <product-form
        @create="createProduct"
    />

    <section class="products">

      <header class="products__header">
        <my-select 
            v-model="selectedSort"
            :options="sortOptions"
        />
      </header>
      <!-- PRODUCT-LIST -->
    <product-list
        :products="products"
        @remove="removeProduct"
        @showDialog="showDialog"
    />
    </section>

    <my-dialog v-model:show="dialogVisible">
        <product-form
            @create="createProduct"
        />
    </my-dialog>
    {{selectedSort}}
  </main>
</template>

<script>
import ProductForm from '@/components/ProductForm.vue'
import ProductList from '@/components/ProductList.vue'

export default {
  components: {
    ProductForm,
    ProductList
  },
  data() {
    return {
        products: [
            {
                id: 1,
                img: require('./assets/img/product-img.png'),
                title: 'Продукт 1',
                description: 'Довольно-таки интересное описание товара в несколько строк.Довольно-таки интересное описание товара в несколько строк',
                price: '10 000'
            },
            {
                id: 2,
                img: require('./assets/img/product-img.png'),
                title: 'Продукт 2',
                description: 'Довольно-таки интересное описание товара в несколько строк.Довольно-таки интересное описание товара в несколько строк',
                price: '10 000'
            },
            {
                id: 3,
                img: require('./assets/img/product-img.png'),
                title: 'Продукт 3',
                description: 'Довольно-таки интересное описание товара в несколько строк.Довольно-таки интересное описание товара в несколько строк',
                price: '10 000'
            },
        ],
        dialogVisible: false,
        selectedSort: '',
        sortOptions: [
            {value: 'title', name: "По наименованию"},
            {value: 'min', name: "По убыванию"},
            {value: 'max', name: "По возрастанию"},

        ]
    }
  },
  methods: {
    createProduct(product){
        this.products.push(product)
        this.dialogVisible = false
    },
    removeProduct(product){
        this.products = this.products.filter(p => p.id !== product.id)
    },
    showDialog(){
        this.dialogVisible = true
    }
  },
};
</script>

<style lang="sass">
@import 'reset-css'
@import url('https://fonts.googleapis.com/css2?family=Cormorant:wght@300;500;600;700&family=Montserrat:wght@100;200;300;400;500;600;800&display=swap')

// MAIN-STYLE
:root
    // COLOR
    --color-secondary: #FFFEFB
    --color-primary: #3F3F3F
    --color-label: #49485E
    --color-placeholder: #B4B4B4

    --color-active: #7BAE73
    --color-disabled: #EEEEEE
    --color-error: #FF8484

    // FONT-SIZE
    --fs-xlarge: 28px
    --fs-large: 24px
    --fs-xmedium: 20px
    --fs-medium: 16px
    --fs-small: 12px
    --fs-form-label: 10px

    //FONT-WEIGHT
    --fw-semi-bold: 600
    --fw-regular: 400

    // FONT-FAMILY
    --ff-primary: 'Source Sans Pro', sans-serif

.main
    padding: 32px
    display: grid
    grid-template-columns:  343px 1fr
    gap: 16px
    font-family: var(--ff-primary)
    background: rgba(255, 254, 251, 0.8)
    color: var(--color-primary)
    line-height: 1.2

.label
    display: flex
    flex-direction: column
    gap: 5px
    &__span
        font-size: var(--fs-form-label)
        color: var(--color-label)
button
    cursor: pointer

// PRODUCTS
.products
    &__header
        display: flex
        justify-content: end


@media (max-width: 480px)
    .main
        grid-template-columns: 1fr

</style>
