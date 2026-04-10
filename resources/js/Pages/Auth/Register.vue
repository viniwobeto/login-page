<script setup>
import { useForm } from '@inertiajs/vue3'

const form = useForm({
  name: '',
  email: '',
  password: '',
  password_confirmation: '',
})
</script>

<template>
  <div class="min-h-screen flex items-center justify-center bg-gradient-to-br from-purple-500 to-indigo-600">
    
    <div class="bg-white w-full max-w-sm p-8 rounded-2xl shadow-xl">
      
      <h1 class="text-2xl font-bold text-center mb-6">Cadastro</h1>

      <form @submit.prevent="form.post('/register')" class="space-y-4">
        
        <div>
          <input v-model="form.name" placeholder="Nome" class="input" />
          <p v-if="form.errors.name" class="text-red-500 text-sm">{{ form.errors.name }}</p>
        </div>

        <div>
          <input v-model="form.email" placeholder="Email" class="input" />
          <p v-if="form.errors.email" class="text-red-500 text-sm">{{ form.errors.email }}</p>
        </div>

        <div>
          <input type="password" v-model="form.password" placeholder="Senha" class="input" />
          <p v-if="form.errors.password" class="text-red-500 text-sm">{{ form.errors.password }}</p>
        </div>

        <div>
          <input type="password" v-model="form.password_confirmation" placeholder="Confirmar senha" class="input" />
        </div>

        <button type="submit" class="btn">
          Cadastrar
        </button>

      </form>

      <p class="text-sm text-center mt-4">
        Já tem conta?
        <a href="/login" class="text-purple-500">Entrar</a>
      </p>

    </div>

  </div>
</template>

<style scoped>
.input {
  width: 100%;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 8px;
}
.btn {
  width: 100%;
  padding: 10px;
  background: #7c3aed;
  color: white;
  border-radius: 8px;
}
</style>