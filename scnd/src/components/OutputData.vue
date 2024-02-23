<template>
    <div>
      <h3>Введенные данные:</h3>
      <div v-for="(value, key) in data" :key="key">
        <strong>{{ key }}:</strong> {{ value }}
      </div>
    </div>
  </template>
  
<script>
export default {
props: {
    data: Object
}
}
</script>

<style scoped>
/* Styles for the OutputData component */
</style>
  