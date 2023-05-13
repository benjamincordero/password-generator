<script setup>
import { ref, onMounted } from 'vue';
const isDark = ref(false);
const darkMode = () => {
  isDark.value = !isDark.value;
  localStorage.setItem("isDark", isDark.value);
  if (isDark.value) {
    document.documentElement.classList.add("dark");
    document.body.classList.add("bg-slate-900");
  } else {
    document.documentElement.classList.remove("dark");
    document.body.classList.remove("bg-slate-900");
  }
  localStorage.setItem("dark", isDark.value.toString());

}

onMounted(() => {
  let ls = localStorage.getItem("dark");
  if (ls == "true") {
    document.documentElement.classList.add("dark");
    document.body.classList.add("bg-slate-900");
    isDark.value = true;
  } else {
    isDark.value = false;
    document.documentElement.classList.remove("dark");
    document.body.classList.remove("bg-slate-900");

  }
  localStorage.setItem("dark", isDark.value.toString());
});

</script>
<template>
  <div class="py-6 pr-6 flex justify-end">
    <button @click="darkMode" class=" p-2 rounded-full text-white hover:bg-slate-700">
      <img src="/yoda.png" v-if="isDark" alt="dark">
      <img src="/vader.png" v-if="!isDark" alt="dark">

    </button>
  </div>
</template>
