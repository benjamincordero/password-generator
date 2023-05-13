<script setup>
import { inject } from 'vue';
const cant = inject('cant');
const generatePassword = inject('generatePassword');
const mayus = inject('mayus');
const minus = inject('minus');
const specialCharacters = inject('specialCharacters');
const numbers = inject('numbers');

</script>
<template>
  <form @submit.prevent="1 + 1" @change="generatePassword">
    <div>
      <label for="default-range" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
        Cantidad de Caracteres
      </label>
      <input id="cant" type="range" min="1" max="50"
        class="w-full h-2 bg-gray-400 rounded-lg appearance-none cursor-pointer " :class="{
          'bg-red-500': cant < 9,
          'bg-yellow-500': cant >= 9 && cant < 20,
          'bg-green-500': cant >= 20
        }
          " v-model="cant" @change="console.log(cant)">
      <p class="text-center font-bold" :class="{
        'text-red-500': cant < 9,
        'text-yellow-500': cant >= 9 && cant < 20,
        'text-green-500': cant >= 20
      }
        ">
        {{ cant }}
      </p>
    </div>

    <div>
      <ul
        class="flex flex-col lg:flex-row text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-lg dark:bg-gray-700 dark:border-gray-600 dark:text-white">
        <li class="w-full border-b border-gray-200 rounded-t-lg dark:border-gray-600">
          <div class="flex items-center pl-3">
            <input id="react-checkbox" type="checkbox" v-model="minus"
              class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500">
            <label for="react-checkbox" class="w-full py-3 ml-2 text-sm font-medium text-gray-900 dark:text-gray-300">
              Minusculas
            </label>
          </div>
        </li>
        <li class="w-full border-b border-gray-200 rounded-t-lg dark:border-gray-600">
          <div class="flex items-center pl-3">
            <input id="vue-checkbox" type="checkbox" v-model="mayus"
              class="w-4 h-4 text-blue-600 bg-gray-100 font-bold border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500">
            <label for="vue-checkbox" class="w-full py-3 ml-2 text-sm font-medium text-gray-900 dark:text-gray-300">
              Mayusculas
            </label>
          </div>
        </li>

        <li class="w-full border-b border-gray-200 rounded-t-lg dark:border-gray-600">
          <div class="flex items-center pl-3">
            <input id="angular-checkbox" type="checkbox" v-model="specialCharacters"
              class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500">
            <label for="angular-checkbox" class="w-full py-3 ml-2 text-sm font-medium text-gray-900 dark:text-gray-300">
              Simbolos
            </label>
          </div>
        </li>
        <li class="w-full border-b border-gray-200 rounded-t-lg dark:border-gray-600">
          <div class="flex items-center pl-3">
            <input id="laravel-checkbox" type="checkbox" v-model="numbers"
              class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500">
            <label for="laravel-checkbox"
              class="w-full py-3 ml-2 text-sm font-medium text-gray-900 dark:text-gray-300">Numeros</label>
          </div>
        </li>
      </ul>
    </div>

  </form>
</template>
