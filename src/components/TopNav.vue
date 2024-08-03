<template>
    <div class="header">
        <nav class="container">
            <div class="logo-content">
                <img src="https://i.imgur.com/sOCVfKv.png" alt="Logo" />
                <span v-if="props.windowWidth >= 480">Anh Khoa</span>
            </div>
            <div class="right-tooltip">
                <template v-if="props.windowWidth >= 768">
                    <ul>
                        <li><a href="#">Indie <span>Game</span></a></li>
                        <li><a href="#">Entry <span>Game</span></a></li>
                        <li><a href="#">Comm<span>unity</span></a></li>
                    </ul>
                </template>
                <template v-else>
                    <button :class="`menu-toggle${stateShow ? ' menu-open' : ''}`" @click="stateShow = !stateShow">
                        <span v-if="!stateShow">&#9776;</span>
                        <span v-else>&#10005;</span>
                    </button>
                </template>
            </div>
            <div v-if="stateShow" :class="`menu-mobile`">
                <ul>
                    <li><a href="#">Indie <span>Game</span></a></li>
                    <li><a href="#">Entry <span>Game</span></a></li>
                    <li><a href="#">Comm<span>unity</span></a></li>
                </ul>
            </div>
        </nav>
    </div>
</template>
<script setup lang="ts">
import { watch, ref } from 'vue';

interface IProps {
    windowWidth: number
}

const props = defineProps<IProps>()

const stateShow = ref(false)

watch(
    () => props.windowWidth,
    (newValue) => {
        if (newValue >= 768) {
            stateShow.value = false
        }
    }
);
</script>