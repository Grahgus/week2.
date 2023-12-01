<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from "vue-router"
import { useAuthStore } from '@/stores/auth'

const auth = useAuthStore()
const username = ref('')
const router = useRouter()

const onLogin = () => {
    auth.login(username.value)

    router.push('/')
}

</script>


<template>
    <div>
        <h1>login page</h1>
        <div class="flex flex-col gap-2">
            {{ username }}
            <input type="text" v-model="username" class="border"/>
            <button @click="onLogin()" class="bg-blue-500 text-white py-1 px-3">login</button>
        </div>
    </div>
</template>