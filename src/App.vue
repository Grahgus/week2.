<script setup lang="ts">
import { useAuthStore } from '@/stores/auth'
import { useRouter } from 'vue-router';
import router from './router';
const auth = useAuthStore()

const onLogout = () => {
  auth.logout()
  router.push('/login')
}
</script>


<template>
  <div class="flex flex-col container mx-auto p-4 gap-10">
    <!--header-->
    <div class="flex justify-between p">
      <!--menu-->
      <div class="flex gap-4">
       <router-link to="/">Home</router-link>
       <router-link to="/about">about</router-link>
       <router-link to="/restricted">restricted page</router-link>
      </div>
      <!--authentification user-->
      <div class="flex gap-2 items-center">
        <p v-if="auth.username">{{ auth.username }}</p>
        <div v-if="auth.username">
          <button class="bg-orange-500 text-white py-1 px-3" @click="onLogout()">Logout</button>
        </div>
        <div v-else>
          <router-link class="bg-blue-500 text-white py-1 px-3" to="/login">login</router-link>
        </div>
      </div>
    </div>
    <!--body-->
    <router-view></router-view>
  </div>
</template>
  