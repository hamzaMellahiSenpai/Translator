<template>
  <div id="output">
    <h2 class="bg-info p-3">{{ text }}</h2>
  </div>
</template>

<script>

export default {
    props:[text]
}
</script>

<style>
h2 {
  font-size: 30px;
  color: white;
}
</style>
