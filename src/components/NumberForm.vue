
<script lang="ts" setup>
import { computed } from 'vue';
// @ts-ignore
import Flag from './Flag.vue';

const props = defineProps<{
    number: string;
}>();

const getFirstSymbol = computed(() => {
    return props.number.length ? props.number[0].toUpperCase() : null;
});

const getNumbers = computed(() => {
    return props.number.slice(2, 5).toUpperCase();
});

const getLastSymbols = computed(() => {
    return props.number.slice(6, 8).toUpperCase();
});

const getRegion = computed(() => {
    return props.number.slice(9, 12).toUpperCase().trim();
});




</script>
<template>
    <div class="number-wrapper">
        <div class="car-number-form">
            <div class="car-number-form__id">
            <span class="symbol">
                {{ getFirstSymbol }}
            </span>
            <span class="symbol">
                {{ getNumbers }}
            </span>
            <span class="symbol">
                {{ getLastSymbols }}
            </span>
            </div>
            <div class="car-number-form__region">
                <span class="symbol">
                    {{ getRegion }}
                </span>
                <div class="car-number-form__region-bottom">
                    <span class="car-number-form__region-text">
                        RUS
                    </span>
                    <Flag />
                </div>
            </div>
        </div>
    </div>
    
</template>

<style lang="sass" scoped>
.number-wrapper
    background-color: #fff
    width: fit-content
    padding: 5px
    border-radius: 14px
    margin: 0 auto
    width: 100%
    @media screen and (min-width: 1200px)
        width: 450px
.car-number-form
    position: relative
    display: grid
    grid-template-columns: 70% 30%
    border: 6px solid #000
    width: 100%
    border-radius: 14px
    max-width: 450px
    margin: 0 auto
    max-height: 100px
    font-family: RoadNumbers
    background-color: #fff
    &::before
        left: 5px
    &::after
        right: 5px
    &__input
        border-radius: 8px
        text-align: center
        letter-spacing: 6px
    &__id
        position: relative
        height: 100%
        display: flex
        font-size: 75px
        align-items: center
        justify-content: center
        letter-spacing: 6px
        height: 80px
        @media screen and (min-width: 1200px)
            font-size: 80px
            letter-spacing: 8px
            padding-bottom: 30px
    &__region
        position: relative
        display: flex
        align-items: center
        justify-content: center
        border-left: 4px solid #000
        font-family: RoadNumbers
        line-height: 1.8
        font-size: 55px
        height: 80px
        padding-bottom: 10px
        @media screen and (min-width: 1200px)
            padding-bottom: 35px
        .symbol
            letter-spacing: 4px
    &__region-bottom
        position: absolute
        bottom: 1px
        left: 50%
        transform: translateX(-50%)
        display: flex
        align-items: center
        justify-content: center
        font-family: sans-serif
        font-weight: 600
        gap: 10px
    &__region-text
        font-size: 16px
</style>