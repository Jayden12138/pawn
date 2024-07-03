<script lang="ts" setup>
import { ref } from 'vue'
const props = defineProps<{
    name: string
    age: number
    sex: string
}>()

const changeCount = ref(0)

const emit = defineEmits(['changeUserName', 'changeUserAge'])

const changeUserName = () => {
    emit('changeUserName', `${props.name}11`)
    changeCount.value++
}

const changeUserAge = () => {
    emit('changeUserAge', `${+props.age + 1}`)
}
</script>

<template>
    <div class="user-info">
        <p>changeCount: {{ changeCount }}</p>
        <p @click="changeUserName">姓名: {{ name }}</p>
        <p @click="changeUserAge">年龄: {{ age }}</p>
        <p>性别: {{ sex }}</p>
    </div>
</template>
