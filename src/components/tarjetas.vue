<script setup>
defineProps(['title','id','texto'])
</script>
<div class="card"></div>
<template>
<div class="card">
    <div class="card-body">
        <h1 class="card-title">{{ id }} {{title}}</h1>
        <p>{{ texto }}</p>
        <button @click="$emit('cambiarnombre' ,title)" class="btn btn-success">aplicar</button>
    </div>
</div>
</template>