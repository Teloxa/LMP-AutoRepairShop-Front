<template>
  <NavbarContent />

  <div class="min-h-[calc(100vh-64px)] flex items-center justify-center bg-slate-50 py-12">
    <div class="container mx-auto px-4">
      <div class="max-w-4xl mx-auto bg-white rounded-lg shadow-lg overflow-hidden md:flex">
        <div
          class="md:w-1/2 bg-gradient-to-br from-sky-600 to-indigo-600 flex items-center justify-center p-8"
        >
          <img
            src=""
            alt=""
            class="hidden md:block w-full h-auto object-cover"
            onerror="this.style.display='none'"
          />
          <!-- Fallback placeholder if image not present -->
          <div class="md:hidden text-white flex items-center justify-center">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-20 w-20"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="1.5"
                d="M3 7v10a2 2 0 002 2h14a2 2 0 002-2V7M7 7V4a2 2 0 012-2h6a2 2 0 012 2v3"
              />
            </svg>
          </div>
        </div>

        <!-- Right: form -->
        <div class="md:w-1/2 p-8">
          <h2 class="text-2xl font-bold mb-4">Welcome back</h2>
          <p class="text-sm text-slate-500 mb-6">Sign in to your account</p>

          <form @submit.prevent="onSubmit" class="space-y-4">
            <div>
              <label for="username" class="block text-sm font-medium text-slate-700 mb-1"
                >Username</label
              >
              <input
                id="username"
                v-model="form.username"
                required
                class="w-full border border-slate-200 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-400"
              />
            </div>

            <div>
              <label for="password" class="block text-sm font-medium text-slate-700 mb-1"
                >Password</label
              >
              <input
                id="password"
                type="password"
                v-model="form.password"
                required
                class="w-full border border-slate-200 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-400"
              />
            </div>

            <div>
              <!-- TASK: @click will remove when I finish the validation for inputs -->
              <button
                type="submit"
                class="w-full bg-sky-600 hover:bg-sky-500 text-white py-2 rounded-md font-semibold"
                @click="$router.push('/dashboard')"
              >
                Log in
              </button>
            </div>
          </form>

          <p class="mt-4 text-sm text-slate-500">
            Don't have an account?
            <router-link to="/register" class="text-sky-600 hover:underline">Register</router-link>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import NavbarContent from '../components/ui/NavbarContent.vue'
import { reactive } from 'vue'

// TASK: Uncomment when ready to use router for redirection
// import { useRouter } from 'vue-router'

// const router = useRouter()
const form = reactive({ username: '', password: '', remember: false })

// function onSubmit() {
//   // TODO: replace with real authentication call
//   console.log('Submitting login', { ...form })
//   // Redirect after successful login (placeholder)
//   router.push('/')
// }
//
</script>
