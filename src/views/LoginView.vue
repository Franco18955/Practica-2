<script setup>
import { reactive } from 'vue'
import { useRouter } from 'vue-router'

import { useAuthStore } from '../stores/auth'

const auth = useAuthStore()
const router = useRouter()

const form = reactive({
  email: '',
  password: ''
})

const login = async () => {

  console.log('Botón funcionando')
  try {
    await auth.login(form)
    console.log('Login correcto')
    window.location.href = '/dashboard'
  } catch (error) {
    console.log(error)
    alert('Error al iniciar sesión')
  }
}
</script>

<template>
  <div>
    <h1>Login</h1>
    <input
      v-model="form.email"
      type="email"
      placeholder="Correo"
    />
    <br><br>
    <input
      v-model="form.password"
      type="password"
      placeholder="Contraseña"
    />
    <br><br>
    <button @click="login">
      Iniciar Sesión
    </button>
  </div>
</template>