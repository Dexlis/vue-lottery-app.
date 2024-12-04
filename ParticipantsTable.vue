<template>
    <div>
      <h2>Winners</h2>
      <ul>
        <li v-for="winner in winners" :key="winner">{{ winner.name }}</li>
      </ul>
      <button @click="chooseWinner" :disabled="!canChooseWinner">
        New winner
      </button>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { ref, computed } from 'vue';
  
  const participants = ref([]);
  const winners = ref([]);
  
  const canChooseWinner = computed(() => participants.value.length > 0 && winners.value.length < 3);
  
  const chooseWinner = () => {
    if (participants.value.length > 0) {
      const winner = participants.value[Math.floor(Math.random() * participants.value.length)];
      winners.value.push(winner);
    }
  };
  </script>