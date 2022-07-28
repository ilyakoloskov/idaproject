<template>
    <div class="dialog" v-if="show" @click.stop="hideDialog">
        <div @click.stop class='dialog__inner'>
            <slot>
            </slot>
        </div>
    </div>
</template>

<script>
    export default {
        name: "my-dialog",
        props: {
            show: {
                type: Boolean,
                default: false
            }
        },
        methods: {
            hideDialog(){
                this.$emit('update:show', false)
            }
        }
    }
</script>

<style lang="sass" scoped>
.dialog
    position: fixed
    left: 0
    right: 0
    bottom: 0
    top: 0
    display: flex
    place-items: center
    background: rgba(0, 0, 0 , 0.5)
    z-index: 99
    &__inner
        box-sizing: border-box
        margin: 0 auto
        background: var(--color-secondary)
        min-width: 60vh
        min-height: 60vh
        padding: 20px 
        box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02)
        border-radius: 10px


</style>