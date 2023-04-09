<script setup>
defineProps(['inicio','fin','title','title2'])

</script>
<template>
    <div class="btn-group" role="group" aria-label="Basic example">
  <button type="button" class="btn btn-success" :disabled=" inicio <= 0"
  @click="$emit('restar')">{{ title }}</button>
  <button type="button" class="btn btn-primary" :disabled=" fin === 100"
  @click="$emit('sumar')">{{ title2 }}</button>
</div>
</template>