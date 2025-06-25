<script setup>
</script>

<template>
    <div class="flag">
        <span class="flag__item flag__item_1"></span>
        <span class="flag__item flag__item_2"></span>
        <span class="flag__item flag__item_3"></span>
    </div>
</template>

<style lang="sass" scoped>
.flag
    width: 22px
    height: 14px
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center
    border: 1px solid #000
    &__item
        display: block
        width: 100%
        flex: 1
        &_1
            background-color: #FFFFFF
        &_2
            background-color: #0039A6
        &_3
            background-color: #D52B1E
</style>