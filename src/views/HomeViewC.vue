<script setup>
import { onMounted, onBeforeMount, computed } from 'vue';
import TheWelcome from '../components/TheWelcome.vue';
onBeforeMount(()=>{
    console.log("we are good")
})
onMounted(() => {
  console.log("hello");
});
const name = computed(()=>{
return 'shaun'
})
</script>

<template>
    <p>{{name}}</p>
  <main>
    <TheWelcome />
  </main>
</template>
