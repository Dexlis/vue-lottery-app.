<template>
    <table class="w-full">
      <thead>
        <tr>
          <th>#</th>
          <th>Name</th>
          <th>Date of Birth</th>
          <th>Email</th>
          <th>Phone</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(participant, index) in participants" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ participant.name }}</td>
          <td>{{ participant.dateOfBirth }}</td>
          <td>{{ participant.email }}</td>
          <td>{{ participant.phone }}</td>
        </tr>
      </tbody>
    </table>
  </template>
  
  <script lang="ts" setup>
  import { ref } from 'vue';
  
  const participants = ref([]);
  </script>