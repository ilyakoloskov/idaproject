<template>
    <select class="select" v-model="modelValue" @change="changeOption">
        <option disabled class="select__option" value="">По умолчанию</option>
        <option 
            v-for="option in options" 
            :key="option.value" 
            class="select__option" 
            :value="option.value">
            {{option.name}}
        </option>
    </select>
</template>

<script>
    export default {
        name: 'my-select',
        props: {
            modelValue: {
                type: String
            },
            options: {
                type: Array,
                default: () => []
            }
        },
        methods: {
            changeOption(event){
                this.$emit('update: modelValue', event.target.value)
            }
        }
    }

</script>

<style lang="sass" scoped>
.select
    padding: 10px 16px
    font-size: var(--fs-small)
    line-height: 1.2
    border: 1px solid transparent
    border-radius: 4px
    background: var(--color-secondary)
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1)
    border-radius: 4px
    -webkit-appearance: none
    background: url(@/assets/icons/arrow-bottom.svg) no-repeat right
    background-position-x: 90%
    color: var(--color-placeholder)
    cursor: pointer
    transition: 0.3s
    &:hover
        transition: 0.3s
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.5)
    &__option
        color: red
    &:focus
        outline: 2px solid var(--color-active)
</style>