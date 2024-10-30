<template>
    <span class="title">{{ title }}</span>
    <p v-html="content"></p>
</template>

<script setup>
defineProps(['title', 'content'])
</script>