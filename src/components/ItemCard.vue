<template>
    <div class="card">
        <img class="wrapper" :src="props.imgUrl" alt="Wrapper" />
        <div class="content">
            Product name is quite long in some cases.
        </div>
    </div>
</template>

<script setup lang="ts">
interface IProps {
    imgUrl: string
}

const props = defineProps<IProps>()
</script>