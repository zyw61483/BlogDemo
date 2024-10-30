<template>
    <div id="aboutme">
        <button @click="content_log">aaaa</button>
        <QuillEditor ref="quillEditorRef" v-model:content="msg" contentType="html" toolbar="full" theme="snow" style="height: 95%;" />
    </div>
</template>

<script setup>
import { ref } from 'vue';

const msg = ref('');
function content_log() {
    console.log(msg.value);
}
</script>
<style>
#aboutme {
    width: 80%;
    height: 90%;
    overflow: hidden;
}
</style>
