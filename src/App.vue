<script setup>
import Taches from './components/Taches.vue'
import TransitData from './components/TransitData.vue'
import { ref } from 'vue';

const messageFromParent = ref('PROPS : hello depuis le parent');
const messageFromChild = ref('fff');

</script>

<template>

  <h1>To Do List de </h1>

  <Taches/>
  <hr>
  <hr>

<!--PROPS-->
  <TransitData 
    :msgprop="messageFromParent"
    @msgEmit="(m) => messageFromChild = m"
  />

<!--EMIT-->
  <p>{{ messageFromChild }}</p>

</template>

<style scoped></style>
