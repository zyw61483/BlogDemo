<template>
    <button id="menu" @click="show = !show">{{ show }}</button>
    <ol id="nav-ol" :class="show ? 'mini-nav' : 'mini-nav-show'">
        <!-- <ol id="nav-ol" v-show="show"> -->
        <li class="nav-li" v-for="item in items">
            <a :href="item.path">{{ item.name }}</a>
        </li>
    </ol>
</template>

<script setup>
import { ref } from 'vue';

const show = ref(true)
const items = ref([{
    path: '#/home', name: 'Home'
}, {
    path: '#/blog', name: 'Blog'
}, {
    path: '#/aboutme', name: 'About Me'
}, {
    path: '#/other', name: '其他'
}])
// defineProps(['items'])
</script>

<style>
a,
a:hover,
a:visited {
    color: #213547;
    text-decoration: none;
}

* {
    border: 0;
    padding: 0;
    margin: 0;
}

#nav-ol {
    color: #213547;
    width: 20%;
    max-width: 240px;
    border-right: 1px solid black;
    height: 100%;
    position: relative;
    font-family: "Bernard MT", "Microsoft YaHei UI";
    font-size: 18px;
}

@media (min-width: 675px) {
    #menu {
        display: none;
    }

    .nav-li {
        display: flex;
        max-width: 300px;
        height: 30px;
        align-items: center;
        justify-content: center;
    }

    .nav-li:hover {
        background-color: #eee;
        cursor: pointer;
        border: 1px solid #ddd;
        border-right: none;
    }

    .mini-nav {
        display: block;
    }
}

@media (max-width: 675px) {

    .mini-nav {
        display: none;
    }

    .mini-nav-show {
        display: block;
    }

    #menu {
        display: block;
        height: 30px;
        background: none;
    }
}
</style>