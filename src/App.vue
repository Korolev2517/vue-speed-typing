<script setup>
import {ref, onMounted} from "vue";

const text = ref('');
const loading = ref(true)

const fetchText = async () => {
  try {
    const response = await fetch('https://fish-text.ru/get');
    const data = await response.json();
    text.value = data.text;
    console.log(text.value);
  } catch (error) {
    console.log('Error', error)
  } finally {
    loading.value = false;
  }
}

onMounted(() => {
  fetchText();
})
</script>

<template>
<div>
  <p class="text">{{ text }}</p>
</div>
</template>

<style scoped>
.text {
  font-size: 20px;
}

</style>
