<script setup lang="ts">
import { ref } from 'vue';
import NumberForm from './components/NumberForm.vue';
/*
в 888 ор 16
а 009 уе 716
а 050 ао 16
у 716 рр 716
р 716 ак 716
у 716 во 716
у 001 нм 116
у 001 во 116
к 001 ас 716
р 999 но 116
о 999 рс 116
у 999 нт 116
в 999 хс 716
в 999 рх 716
е 999 на 716
т 888 тр 116
у 888 мо 116
в 888 хм 716
т 777 мр 116
а 777 ме 116
в 555 тр 116
р 444 ме 116
е 444 тс 716
*/
const textareaModel = ref('');
const isTextareaOpened = ref(true);
const numbers = ref<string[]>([]);

function fillData () {
  if(textareaModel.value.length === 0) {
    return;
  }
  numbers.value = textareaModel.value.split('\n');
  isTextareaOpened.value = false;
}

</script>

<template>
  <div class="wrapper">
    <div v-if="isTextareaOpened" class="textarea-wrapper">
      <button @click="fillData" class="apply-button">Готово</button>
      <textarea 
        v-model="textareaModel" 
        name="data" 
        id="data" 
        class="textarea"
        placeholder="Список номеров. Каждый номер на отдельной строке.в 888 ор 16"
      ></textarea>
    </div>
    <div class="numbers">
      <NumberForm v-for="number in numbers" :key="number" :number="number" />
    </div>
    
  </div>
</template>

<style scoped lang="sass">
.wrapper
  width: 100%

.textarea-wrapper
  position: fixed
  inset: 0
  width: 100vw
  height: 100vh
  display: flex
  flex-direction: column
  gap: 15px
  justify-content: center
  align-items: center
  background-color: rgba(0, 0, 0, 0.4)
  backdrop-filter: blur(10px)
  z-index: 10

.textarea
  display: block
  height: 70%
  width: 90%
  font-size: 16px
  padding: 20px
  font-family: sans-serif
  resize: none
  border: 2px solid #000
  border-radius: 10px

.numbers
  padding: 30px 0
  display: grid
  grid-template-columns: 1fr
  justify-content: center
  align-items: center
  gap: 20px
  @media screen and (min-width: 960px)
    grid-template-columns: 1fr 1fr
  @media screen and (min-width: 1568px)
    grid-template-columns: 1fr 1fr 1fr
  
.apply-button
  padding: 10px 20px
  color: #000
  background-color: #fff
  border: none
  font-size: 16px
  border-radius: 5px
  cursor: pointer
</style>
