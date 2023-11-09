<script setup lang="ts">
import { ref, computed } from 'vue'

const data = {
  'HTML': 'The HyperText Markup Language or HTML is the standard markup language for documents designed to be displayed in a web browser.',
  'CSS': 'Cascading Style Sheets is a style sheet language used for describing the presentation of a document written in a markup language such as HTML or XML.',
  'JavaScript': 'JavaScript, often abbreviated as JS, is a programming language that is one of the core technologies of the World Wide Web, alongside HTML and CSS.'
}

let activeKey = ref('HTML')

let activeTabText = computed(()=>{
  return data[activeKey.value]
}) 

const handleClick = (newKey: string) => {
  activeKey.value = newKey;
}
</script>

<template>
  <div v-for="currentKey of Object.keys(data)" :class="{ active: currentKey === activeKey }">
    <span @click="handleClick(currentKey)">{{ currentKey }}</span>
  </div>
  <div>{{ activeTabText }}</div>
</template>

<style scoped>
.active {
  color: blue;
}
</style>
