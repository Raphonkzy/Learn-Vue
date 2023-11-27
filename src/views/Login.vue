<script setup lang="ts">
import { useRouter } from 'vue-router';
import { useAuthStore } from "@/stores/auth"
import { ref } from 'vue';

const authStore = useAuthStore()
const router = useRouter()

const username = ref("")
const password = ref("")

const usernameValid = "raffa"
const passwordValid = "1234"

const login = (e) => {
    e.preventDefault()
    if (username.value == usernameValid && password.value == passwordValid) {
        console.log(username.value)
        console.log(password.value)

        authStore.username = username.value
        authStore.password = password.value

        router.push("/")
    }
}
</script>

<template>
    <form @submit="(e) => login(e)">
        <div>
            <input type="text" placeholder="Username: raffa" v-model="username">
        </div>
        <div>
            <input type="password" placeholder="Password: 1234" v-model="password">
        </div>
        <button type="submit" class="login">Login</button>
    </form>
</template>