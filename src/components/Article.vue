<template>
    <span class="title">{{ title }}</span>
    <p>{{ content }}</p>
</template>

<script setup>
defineProps(['title', 'content'])
</script>