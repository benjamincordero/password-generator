<script setup>
import { onMounted, ref, provide } from 'vue';
import DarkMode from './components/DarkMode.vue';
import InputPassword from './components/InputPassword.vue';
import SettingsForm from './components/SettingsForm.vue';
const cant = ref(12);
const mayus = ref(true);
const minus = ref(true);
const specialCharacters = ref(true);
const numbers = ref(true);
const password = ref('password');


const generatePassword = () => {
  //generate random password 
  let randomPassword = '';
  let characters = '';
  if (mayus.value) characters += 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  if (minus.value) characters += 'abcdefghijklmnopqrstuvwxyz';
  if (specialCharacters.value) characters += '!@#$%^&*()_+~`|}{[]:;?><,./-='
  if (numbers.value) characters += '0123456789';
  for (let i = 0; i < cant.value; i++) {
    randomPassword += characters.charAt(Math.floor(Math.random() * characters.length));
  }
  password.value = randomPassword;

};

const parpadeo = ref(false);
const typedText = ref('');
const typeWriter = () => {
  const text = 'Pa$$w0rd Gen3rat0r';
  let i = 0;
  const speed = 100;
  const type = () => {
    if (i < text.length) {
      typedText.value += text.charAt(i);
      i++;
      setTimeout(type, speed);
    } else {
      parpadeo.value = true;

    }
  };
  type();
}


//provides
provide('cant', cant);
provide('password', password);
provide('generatePassword', generatePassword);
provide('mayus', mayus);
provide('minus', minus);
provide('specialCharacters', specialCharacters);
provide('numbers', numbers);

onMounted(() => {
  typeWriter();
  generatePassword();
});
</script>

<template>
  <div class="dark:bg-slate-900">
    <DarkMode />

    <h1 class="text-6xl font-bold text-slate-600 dark:text-gray-400 text-center" id="title">
      {{ typedText }}<span class="dark:text-gray-400" :class="{ parpadeo }">|</span>
    </h1>
    <div class="w-3/4 mx-auto lg:mt-20 bg-white dark:bg-slate-800 rounded-md p-6">
      <InputPassword />
      <SettingsForm />
      <br />
    </div>
  </div>
</template>
<style scoped>
@keyframes parpadeo {
  0% {
    opacity: 1;
  }

  50% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}

/* Aplicamos la animación a la letra */
.parpadeo {
  animation: parpadeo 1s infinite;
}
</style>
