<script setup>
import { usePage, router, Link } from '@inertiajs/vue3'

const page = usePage()
const user = page.props.auth.user

const logout = () => {
  router.post('/logout')
}
</script>

<template>
  <nav class="fixed top-0 left-0 w-full bg-gradient-to-r from-indigo-500 to-purple-600 text-white shadow z-50">
    
    <div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between">

      <div class="flex items-center gap-6">
        
        <span class="text-lg font-bold">
          MeuSistema
        </span>

        <Link
          href="/dashboard"
          class="text-white/80 hover:text-white transition"
        >
          Dashboard
        </Link>

      </div>

      <div class="flex items-center gap-4">

        <span class="text-sm">
          Olá, <strong>{{ user?.name }}</strong>
        </span>

        <button
          @click="logout"
          class="text-sm text-white/80 hover:text-red-200 transition"
        >
          Sair
        </button>

      </div>

    </div>

  </nav>
</template>