<script setup>

import { useRouter } from 'vue-router'
import { useAuthStore } from '../stores/auth'

const auth = useAuthStore()
const router = useRouter()

const logout = async () => {

  await auth.logout()

  router.push('/login')
}

</script>

<template>

  <div>

    <h1>Dashboard</h1>

    <h2>
      Bienvenido {{ auth.user?.name }}
    </h2>

    <br>

    <button @click="logout">
      Cerrar Sesión
    </button>

  </div>

</template>