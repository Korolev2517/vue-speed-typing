<script setup>
import {ref} from "vue";

const inputText = ref('');

</script>

<template>
<div class="input-area">
  <p>{{ inputText }}</p>
</div>
</template>

<style scoped>
.input-area {
  width: 100%;
  height: 200px;
  padding: 5px 10px;
  box-sizing: border-box;
  border: 1px solid black;
}
</style>