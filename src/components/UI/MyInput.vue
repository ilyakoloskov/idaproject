<template>
    <label class="label" :for="id">
        <span class="label__span">{{name}}</span>
        <input
            class="label__input"
            :class="{invalid: error}"
            :value="modelValue"
            @input="updateInput"
            :id="id"
            type="text"
            :placeholder="placeholder"
        >
        <small v-if="error" class='label__error'>{{error}}</small>
    </label>
</template>

<script>
export default {
    name: 'my-input',
    props: {
        modelValue: [String, Number],
        name: {
            type: String
        },
        id: {
            type: String
        },
        placeholder: {
            type: String
        },
        error: {
            type: String
        }
    },
    methods: {
        updateInput(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    }       
}
</script>

<style lang="sass" scoped>
.label
    &__input
        background: var(--color-secondary)
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1)
        border-radius: 4px
        padding: 10px 0 10px 15px
        border: none
        outline: none
        font-family: var(--ff-primary)
        font-size: var(--fs-small)
        color: var(--color-label)
        border: 1px solid transparent
        transition: 0.2s

        &::placeholder
            font-size: var(--fs-small)
            color: var(--color-placeholder)
        &:focus
            outline: 2px solid var(--color-active)
        &:hover
            transform: scale(1.1)
            transition: 0.1s
            box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.3)
    &__error
        font-size: var(--fs-small)
        color: var(--color-error)
.invalid
    outline: 2px solid var(--color-error) !important
</style>