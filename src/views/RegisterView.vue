<script setup>
import { reactive } from 'vue'
import { useRouter } from 'vue-router'

import { useAuthStore } from '../stores/auth'

const auth = useAuthStore()
const router = useRouter()

const form = reactive({
  name: '',
  email: '',
  password: '',
  password_confirmation: ''
})

const register = async () => {
  try {
    await auth.register(form)
    window.location.href = '/dashboard'
  } catch (error) {
    console.log(error.response.data.errors)
    alert('Error al registrarse')
  }
}
</script>

<template>
  <div>
    <h1>Registro</h1>
    <input
      v-model="form.name"
      placeholder="Nombre"
    />
    <br><br>
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
    <input
      v-model="form.password_confirmation"
      type="password"
      placeholder="Confirmar contraseña"
    />
    <br><br>
    <button @click="register">
      Registrarse
    </button>
  </div>
</template>