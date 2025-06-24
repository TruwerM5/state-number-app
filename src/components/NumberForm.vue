
<script lang="ts" setup>
import { ref, reactive } from 'vue';
import Flag from './Flag.vue';
const region_input = ref<any>();
const id_input = ref<any>();
const error_message = ref('');

const state = reactive({
    id_value: '',
    region_value: '',
    numbers: '',
    characters: '',
    allowed_characters: 'АВЕКМНОРСТУХ1234567890'
});



function uppercaseNumberId() {
    state.id_value = state.id_value.toUpperCase(); 
}

function onKeyUp(e:any) {
    // let value = e.target.value.toUpperCase();
    uppercaseNumberId();
    
    let filtered_2 = [];
    let filtered = state.id_value.split('')
    .filter(char => {
        if(state.allowed_characters.includes(char)) {
            return true
        } else {
            error_message.value = 'Введен неверный символ. Разрешены следующие символы АВЕКМНОРСТУХ1234567890'
            return false;
        }
        
    })
    // .filter(char => {
    //     if(
    //     (symbols.includes(char[0]) || !char[0]) && 
    //     () &&
    //     (Number(char[2]) || !char[2]) &&
    //     (Number(char[3] || !char[3])) &&
    //     (symbols.includes(char[4]) || !char[4]) &&
    //     (symbols.includes(char[5]) || !char[5])
    //     ){
            
    //         return true;
    //     } else {
    //         console.log('Dismatch',numberStore.id_value.length < 2);
    //         console.log(char[1])
    //         return false;
    //     }
        
    // })

    if(filtered.length > 0) {
        if(!Number(filtered[0]) && typeof filtered[0] == 'string' && Number(filtered[0]) != 0) {
            filtered_2.push(filtered[0]);
        }
        if(filtered.length > 1) {
            if(Number(filtered[1]) > -1) {
                filtered_2.push(filtered[1])
            }
            if(filtered.length > 2) {
                if(Number(filtered[2]) > -1) {
                    filtered_2.push(filtered[2]);
                }
                if(filtered.length > 3) {
                    if(Number(filtered[3]) > -1) {
                        filtered_2.push(filtered[3])
                    }
                    if(filtered.length > 4) {
                        if(!Number(filtered[4]) && typeof filtered[4] == 'string' && Number(filtered[4]) != 0) {
                            filtered_2.push(filtered[4])
                        }
                        if(filtered.length > 5) {
                            if(!Number(filtered[5]) && typeof filtered[5] == 'string' && Number(filtered[5]) != 0) {
                            filtered_2.push(filtered[5])
                            }
                        }
                    }
                }
            }
        }
    }

    filtered = filtered_2;
    state.id_value = filtered_2.join('');
    if(state.id_value.length == 6) {
        region_input.value.focus();
    }

    
}


function onRegionKeyUp() {
    let filtered = state.region_value
    .split('')
    .filter(char => Number(char) > -1)
    .join('');
    state.region_value = filtered;
}


</script>
<template>
    <div class="car-number-form" @click="id_input.focus()">
        
        <div class="car-number-form__id">
            <input type="text" name="number_id" id="number_id" 
            maxlength="6" minlength="6"
            placeholder="М707РН"
            class="car-number-form__input car-number-form__id-input"
            v-model="state.id_value"
            @keyup="onKeyUp"
            ref="id_input"
            pattern="[АВЕКМНОРСТУХ1234567890]*">
        </div>
        <div class="car-number-form__region">
            <input type="text" name="number_region" id="number_region" 
            minlength="2" maxlength="3"
            placeholder="716"
            v-model="state.region_value"
            ref="region_input"
            class="car-number-form__input car-number-form__region-input"
            style="top: 25px;"
            @keyup="onRegionKeyUp">
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
    max-width: 425px
    margin: 0 auto
    font-family: RoadNumbers
    // &::before,
    // &::after
    //     position: absolute
    //     top: 50%
    //     transform: translateY(-50%)
    //     content: ""
    //     width: 5px
    //     height: 5px
    //     border-radius: 50%
    //     border: 2px solid #000
    &::before
        left: 5px
    &::after
        right: 5px
    &__input
        border-radius: 8px
        text-align: center
        letter-spacing: 2px
        font-family: RoadNumbers, sans-serif
        letter-spacing: 6px
    &__id
        position: relative
        height: 90px
    &__input
        position: absolute
        top: -13px
        height: 80px
        z-index: 0
        z-index: -1
    &__id-input
        padding-block: 5px
        padding-left: 10px
        font-size: 80px
    &__region
        position: relative
        border-left: 4px solid #000
        font-family: sans-serif
        line-height: 1.8
        &::before,
        &::after
            position: absolute
            display: block
            content: ""
            left: -2px
            transform: translateX(-50%)
            width: 0
            height: 0
            border-left: 6px solid transparent
            border-right: 6px solid transparent
        &::before
            top: 0
            border-top: 6px solid black
        &::after
            bottom: 0
            border-bottom: 6px solid black
            
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