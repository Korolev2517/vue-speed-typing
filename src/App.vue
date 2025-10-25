<script setup>
import {ref, onMounted} from "vue";
import InputAreaComp from './components/InputAreaComp.vue'

const text = ref('');
const loading = ref(true)

const fetchText = async () => {
  try {
    const response = await fetch('https://fish-text.ru/get');
    const data = await response.json();
    text.value = data.text;
    console.log(text.value);
  } catch (error) {
    console.log('Error', error);
  } finally {
    loading.value = false;
  }
}

onMounted(() => {
  fetchText();
})
</script>

<template>
<div class="wrapper">
  <div class="text-area">
    <p>{{ text }}</p>
  </div>
  <InputAreaComp />
</div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 100%;
  gap: 10px;
}
.text-area {
  width: 100%;
  padding: 5px 10px;
  font-size: 20px;
  border: 1px solid black;
  box-sizing: border-box;
}

</style>
