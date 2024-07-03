<script setup lang="ts">
defineProps({
    imgSrc: {
        required: true,
        type: String,
        default: ''
    },
    imgCustomClass: {
        required: true,
        type: String,
        default: '',
        validator: (value: string) => {
            return ['square', 'rounded'].includes(value)
        }
    }
})
</script>

<template>
    <img :src="imgSrc" :class="imgCustomClass" alt="" />
</template>

<style scoped>
img {
    width: 200px;
    height: auto;
}

.square {
    border-radius: 0;
}
.rounded {
    border-radius: 20px;
}
</style>
