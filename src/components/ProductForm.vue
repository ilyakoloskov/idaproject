<template>
    <div class="form__wrap">
      <h2 class="form__title">Добавление товара</h2>
      <form class="form" @submit.prevent>
        <!-- PRODUCT-NAME -->
        <my-input
          :name="'Наименование товара'"
          :id="'product-name'"
          :placeholder="'Введите наименование товара'"
          v-model.trim="product.title"
          :error="errors.title"
        />
        <!-- PRODUCT-DESCR -->
        <my-textarea
          :name="'Описание товара'"
          :id="'product-description'"
          :placeholder="'Введите описание товара'"
          v-model.trim="product.description"
         />
        <!-- PRODUCT-LINK-IMG -->
        <my-input
          :name="'Ссылка на изображение'"
          :id="'product-link-img'"
          required
          :placeholder="'Введите ссылку'"
          v-model.trim="product.img"
          :error="errors.img"
        />
        <!-- PRODUCT-PRICE -->
        <my-input
          :name="'Цена товара'"
          :id="'product-price'"
          :placeholder="'Введите цену'"
          v-model="product.price"
          :error="errors.price"
        />
        <my-button 
            :class="{
              'btn_active': this.product.img.length > 8 || this.product.title.length > 5 || this.product.price.length > 3,
              'btn_disabled': this.product.img.length < 8 || this.product.title.length < 5 || this.product.price.length < 3 
            }"
            @click="createProduct"
          >Добавить товар
        </my-button>
      </form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            product: {
                title: '',
                description: '',
                img: '',
                price: '',
            },
            errors: {
              name: null,
              img: null,
              price: null
            }
        }
    },
    methods: {
        createProduct(){
          if(this.formIsValidate()){
            this.product.id = Date.now()
            this.$emit('create', this.product)
            this.product = {
                title: '',
                description: '',
                img: '',
                price: '',
            }
          }
        },
        formIsValidate(){
          let isValid = true
          if(this.product.img.length < 8 || this.product.title.length < 5 || this.product.price.length < 3){
            this.errors.img = 'Поле является обязательным, не менее 8 символов'
            this.errors.title = 'Поле является обязательным, не менее 5 символов'
            this.errors.price = 'Поле является обязательным, не менее 3 символов'
            isValid = false
          }else{
            this.errors.img = null
            this.errors.title = null
            this.errors.price = null
          }
          return isValid
        }
    },
}
</script>

<style lang="sass" scoped>
.form
  background: var(--color-secondary)
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02)
  border-radius: 4px
  box-sizing: border-box
  position: sticky
  top: 24px
  display: flex
  flex-direction: column
  gap: 16px
  padding: 24px
  transition: 0.3s
  &__title
      font-size: var(--fs-xlarge)
      margin-bottom: 16px
      line-height: 1.4
  &:hover
    transition: 0.3s
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.1), 0px 6px 10px rgba(0, 0, 0, 0.1)

</style>