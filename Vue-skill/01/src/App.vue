<script setup lang="ts">
import { reactive } from 'vue'

const userInfo1 = reactive({
    name: '张三',
    age: 20,
    sex: '男'
})

const userInfo2 = reactive({
    name: '李四',
    age: 21,
    sex: '女'
})

const handleUserName = (userInfo: any, newName: string) => {
    userInfo.name = newName
}

const handleUserAge = (userInfo: any, newAge: number) => {
    userInfo.age = newAge
}

const userEventHandlers = (userInfo: any) => ({
    changeUserName: (newName: string) => handleUserName(userInfo, newName),
    changeUserAge: (newAge: number) => handleUserAge(userInfo, newAge)
})
</script>

<template>
    <div class="container">
        <div class="user-info-container">
            <UserInfo
                :name="userInfo1.name"
                :age="userInfo1.age"
                :sex="userInfo1.sex"
                @changeUserName="handleUserName(userInfo1, $event)"
                @changeUserAge="handleUserAge(userInfo1, $event)"
            />
            <UserInfo v-bind="userInfo2" v-on="userEventHandlers(userInfo2)" />
        </div>
        <div class="img-container">
            <Img
                imgSrc="https://www.naturalearthdata.com/wp-content/uploads/2018/05/brazil-ne-4d1-names-languages.gif"
                imgCustomClass="rounded"
            />
        </div>
    </div>
</template>

<style scoped></style>
