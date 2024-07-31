<template>
    <div class="card">
        <img class="wrapper" :src="props.imgUrl" alt="Wrapper" />
        <div class="content" :style="{ width: `${props.widthContent}px` }">
            Product name is quite long in some cases.
        </div>
    </div>
</template>

<script setup lang="ts">
interface IProps {
    imgUrl: string
    widthContent: number
}

const props = defineProps<IProps>()
</script>

<style scoped></style>