<script setup>
import { inject } from 'vue';
const copy = () => {
  navigator.clipboard.writeText(password.value);
}
const cant = inject('cant');
const password = inject('password');
const generatePassword = inject('generatePassword');
</script>
<template>
  <div class="mb-6 flex gap-1">
    <button @click="generatePassword" class="bg-gray-200 hover:bg-gray-300 focus:bg-gray-100 p-4 rounded-lg">
      <img src="/refresh.png" alt="refesh">
    </button>
    <input type="text" readonly="true" v-model="password" class="
        block w-full text-center p-4 text-3xl text-gray-700 border border-gray-300 rounded-md bg-gray-50 sm:text-md focus:ring-blue-500 focus:border-blue-500 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500
        " :class="{
          'bg-red-500 dark:bg-red-700': cant < 9,
          'bg-yellow-500 dark:bg-yellow-700': cant >= 9 && cant < 20,
          'bg-green-500 dark:bg-green-700': cant >= 20
        }">
    <button @click="copy" class="bg-gray-200 hover:bg-gray-300 focus:bg-gray-100 p-4 rounded-lg">
      <img src="/copy.png" alt="copy">
    </button>
  </div>
</template>
