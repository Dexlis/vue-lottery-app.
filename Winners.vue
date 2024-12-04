<template>
    <form @submit.prevent="onSubmit" class="flex flex-col gap-4">
      <input
        v-model="name"
        type="text"
        placeholder="Name"
        :class="{'border-red-500': nameError}"
      />
      <input
        v-model="dateOfBirth"
        type="date"
        placeholder="Date of Birth"
        :max="maxDate"
        :class="{'border-red-500': dateError}"
      />
      <input
        v-model="email"
        type="email"
        placeholder="Email"
        :class="{'border-red-500': emailError}"
      />
      <input
        v-model="phone"
        type="tel"
        placeholder="Phone number"
        :class="{'border-red-500': phoneError}"
      />
      <button type="submit" :disabled="!isValid" class="bg-blue-500 text-white">
        Save
      </button>
    </form>
  </template>
  
  <script lang="ts" setup>
  import { ref, computed } from 'vue';
  

  const name = ref('');
  const dateOfBirth = ref('');
  const email = ref('');
  const phone = ref('');
  

  const nameError = computed(() => !name.value);
  const dateError = computed(() => !dateOfBirth.value || new Date(dateOfBirth.value) > new Date());
  const emailError = computed(() => !/^\S+@\S+\.\S+$/.test(email.value));
  const phoneError = computed(() => !/^\(\d{3}\)\s\d{3}-\d{4}$/.test(phone.value));
  

  const maxDate = computed(() => {
    const today = new Date();
    return today.toISOString().split('T')[0]; 
  });
  
  const isValid = computed(() => !nameError.value && !dateError.value && !emailError.value && !phoneError.value);
  
  const onSubmit = () => {

  };
  </script>