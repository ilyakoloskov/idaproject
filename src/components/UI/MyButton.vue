<template>
    <button class="btn" type="submit">
        <slot></slot>
    </button>
</template>

<script>
    export default {
        name: 'my-button',
    }
</script>

<style lang="sass" scoped>
.btn
  font-size: var(--fs-small)
  padding: 10px 0
  border-radius: 10px
  border: none
  outline: none
  &_active
      background: var(--color-active)
      color: var(--color-secondary)
  &_disabled
    background: var(--color-disabled)
    color: var(--color-placeholder)
    cursor: not-allowed
    pointer-events: all !important

</style>