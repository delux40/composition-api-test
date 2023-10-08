<template>
  <section class="container">
    <user-info :first-name="firstName" :last-name="lastName" @setNewAge="setNewAge"></user-info>
  </section>
</template>

<script setup>
import { ref, watch, provide, onBeforeMount, onMounted }  from 'vue'
import UserInfo from './components/UserInfo.vue'

onBeforeMount(() => {
  console.log('onBeforeMount')
})

onMounted(() => {
  console.log('onMounted')
})

const firstName = ref('Dmitry')
const lastName = ref('Burkin')
const uAge = ref(25)

provide('uAge', uAge)

watch(uAge, (value) => {
  if(value > 100) {
    alert('It`s too much!')
    uAge.value = 25
  }
})

function setNewAge(age) {
  uAge.value = age + 10
}

</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>