<script setup lang="ts">
defineProps<{ foo?: string }>();
</script>
<template>
  <div>{{ foo }}</div>
</template>
<style scoped>
.foo-component {
  color: #888;
}
</style>
