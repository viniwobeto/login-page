<script setup>
import { ref, onMounted, computed } from 'vue'
import axios from 'axios'
import Header from '@/Components/Header.vue'

const users = ref([])

const searchName = ref('')
const searchEmail = ref('')

const headers = [
  { text: "ID", value: "id" },
  { text: "Nome", value: "name" },
  { text: "Email", value: "email" },
]

const filteredUsers = computed(() => {
  return users.value.filter(user =>
    user.name.toLowerCase().includes(searchName.value.toLowerCase()) &&
    user.email.toLowerCase().includes(searchEmail.value.toLowerCase())
  )
})

onMounted(async () => {
  const response = await axios.get('/users')
  users.value = response.data
})
</script>
<template>
  <div class="min-h-screen bg-gradient-to-br from-indigo-500 to-purple-600">
    
    <Header />

    <div class="pt-24 px-4">

      <div class="max-w-6xl mx-auto">

        <div class="mb-6 text-white">
          <h1 class="text-3xl font-bold">Dashboard</h1>
          <p class="text-white/80">Gerenciamento de usuários</p>
        </div>

        <div class="bg-white rounded-2xl shadow-xl p-6">

        <div class="flex flex-col md:flex-row gap-3 mb-5">
        
        <input
            v-model="searchName"
            type="text"
            placeholder="Buscar nome..."
            class="w-full md:w-1/3 px-3 py-1.5 text-sm border border-gray-300 rounded-md focus:ring-2 focus:ring-indigo-400 focus:border-indigo-400 outline-none transition"
        />

        <input
            v-model="searchEmail"
            type="text"
            placeholder="Buscar email..."
            class="w-full md:w-1/3 px-3 py-1.5 text-sm border border-gray-300 rounded-md focus:ring-2 focus:ring-indigo-400 focus:border-indigo-400 outline-none transition"
        />

        </div>

          <EasyDataTable
            :headers="headers"
            :items="filteredUsers"
            alternating
            border-cell
            table-class-name="custom-table"
          />

        </div>

      </div>

    </div>

  </div>
</template>