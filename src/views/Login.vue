<template>
  <section>
    <form @submit.prevent="onSubmit" class="max-w-md p-4 m-4 bg-gray-500">
      <label for="email">Correo electronico:</label>
      <input type="email" id="email" placeholder="ejemplo@gmail.com" v-model="credentials.email">
      <label for="password">Contraseña:</label>
      <input :type="visible ? 'text' : 'password'" id="password" placeholder="Contraseña" v-model="credentials.password">
      <button @click.prevent="toggleShowPassword">{{ visible ? "hide password" : "show password" }}</button>
      <button type="submit">Log In</button>
    </form>

    <button @click.prevent="getData">Get data</button>

  </section>
</template>

<script setup>
import axios from 'axios'
import { ref, reactive } from 'vue'
import Cookies from 'js-cookie'

const visible = ref(false)
const credentials = reactive({
  email: '',
  password: ''
})

function toggleShowPassword() {
  return visible.value = !visible.value
}

const onSubmit = async () => {
  if (!credentials.email || !credentials.password) return alert('Please enter an email and a passowrd')
  const data = await axios.post('http://localhost:3001/api/signin', credentials)
console.log(data);
  console.log(document.cookie);
}

const cookie = Cookies.get('token');

const getData = async () => {
  const { data } = await axios.get('http://localhost:3001/api/profile', {
    headers: {
      token: cookie
    }
  })
  console.log(data)
}
</script>

<style lang="scss" scoped></style>