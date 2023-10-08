<template>
  <h2>{{ fullName }}</h2>
  <h3>{{ age }}</h3>
  <button @click="sendEvent">Change Age</button>
</template>

<script setup>
import { defineProps, defineEmits, computed, inject } from 'vue'

const age = inject('uAge')

const props = defineProps(['firstName', 'lastName'])
const emit = defineEmits(['setNewAge'])

const fullName = computed(() => {
  return props.firstName + ' ' + props.lastName
})

function sendEvent() {
  emit('setNewAge', age.value)
}

</script>