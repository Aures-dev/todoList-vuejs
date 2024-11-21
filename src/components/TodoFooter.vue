<script setup>
// eslint-disable-next-line no-unused-vars
const props = defineProps({
  count: Number
})
</script>

<template>
    <p class="box">Il vous reste {{ count }} tâches à éffectuer</p>
</template>

<style scoped>
p{
  background-color: hsl(42deg 100% 52.94%);
}
</style>