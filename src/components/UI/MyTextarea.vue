<template>
    <label class="label" :for="id">
        <span class="label__span">{{name}}</span>
        <textarea
        :value="modelValue"
        @input="updateTextarea"
        class="label__textarea"
        :id="id"
        type="text"
        :placeholder="placeholder"
        ></textarea>
    </label>
</template>

<script>
export default {
    name: 'my-textarea',
    props: {
        modelValue: String,
        name: {
            type: String
        },
        id: {
            type: String
        },
        placeholder: {
            type: String
        }
    },
    methods: {
        updateTextarea(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>

<style lang="sass" scoped>
.label
    &__textarea
        background: var(--color-secondary)
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1)
        border-radius: 4px
        padding: 10px 15px
        border: none
        outline: none
        font-family: var(--ff-primary)
        font-size: var(--fs-small)
        color: var(--color-label)
        min-height: 108px
        resize: none
        &::placeholder
            font-size: var(--fs-small)
            color: var(--color-placeholder)
        &:focus
            outline: 2px solid var(--color-active)
</style>