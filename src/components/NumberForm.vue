
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
    return props.number.slice(9).toUpperCase();
});




</script>
<template>
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
</template>

<style lang="sass" scoped>

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
        @media screen and (min-width: 1568px)
            font-size: 80px
            letter-spacing: 8px
            padding-bottom: 10px
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
        padding-bottom: 40px
        .symbol
            letter-spacing: 4px
    &__region-input
        display: block
        position: absolute
        top: 40%
        height: fit-content
        width: fit-content
        transform: translateY(-50%)
        font-size: 65px
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
    &__region-icon
        width: 20px
    &__region-text
        font-size: 14px
</style>