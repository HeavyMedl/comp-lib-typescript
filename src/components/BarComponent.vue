<script setup lang="ts">
defineProps<{ bar?: string }>();
</script>
<template>
  <div>{{ bar }}</div>
</template>
<style scoped>
.bar-component {
  color: #888;
}
</style>
