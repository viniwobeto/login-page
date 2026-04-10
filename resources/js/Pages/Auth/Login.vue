<script setup>
import { useForm } from '@inertiajs/vue3'

const form = useForm({
  email: '',
  password: '',
})
</script>

<template>
  <div class="min-h-screen flex items-center justify-center bg-gradient-to-br from-indigo-500 to-purple-600">
    
    <div class="bg-white w-full max-w-sm p-8 rounded-2xl shadow-xl">
      
      <h1 class="text-2xl font-bold text-center mb-6">Login</h1>

      <form @submit.prevent="form.post('/login')" class="space-y-4">
        
        <div>
          <input
            v-model="form.email"
            type="email"
            placeholder="Email"
            class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-indigo-400 outline-none"
          />
          <p v-if="form.errors.email" class="text-red-500 text-sm mt-1">
            {{ form.errors.email }}
          </p>
        </div>

        <div>
          <input
            v-model="form.password"
            type="password"
            placeholder="Senha"
            class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-indigo-400 outline-none"
          />
          <p v-if="form.errors.password" class="text-red-500 text-sm mt-1">
            {{ form.errors.password }}
          </p>
        </div>

        <p v-if="form.errors.email || form.errors.password" class="text-red-500 text-sm text-center">
          Credenciais inválidas
        </p>

        <button
          type="submit"
          class="w-full bg-indigo-500 text-white py-2 rounded-lg hover:bg-indigo-600 transition"
          :disabled="form.processing"
        >
          {{ form.processing ? 'Entrando...' : 'Entrar' }}
        </button>

      </form>

      <p class="text-sm text-center mt-4">
        Não tem conta?
        <a href="/register" class="text-indigo-500 hover:underline">Cadastrar</a>
      </p>

    </div>

  </div>
</template>