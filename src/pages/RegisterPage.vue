<template>
  <NavbarContent />

  <div class="min-h-[calc(100vh-64px)] flex items-center justify-center bg-slate-50 py-12">
    <div class="container mx-auto px-4">
      <div class="max-w-5xl mx-auto bg-white rounded-lg shadow-lg overflow-hidden md:flex">
        <div
          class="md:w-1/2 bg-gradient-to-br from-sky-600 to-indigo-600 flex items-center justify-center p-0 h-full overflow-hidden"
        >
          <img
            src="@/assets/login-image2.jpg"
            alt="Login image"
            class="w-full h-full object-cover rounded-l-lg"
            onerror="this.style.display='none'"
          />
        </div>

        <!-- Right: form -->
        <div class="md:w-1/2 p-8 flex flex-col h-full justify-center">
          <h2 class="text-2xl font-bold mb-4 text-center">SIGN UP</h2>
          <p class="text-sm text-slate-500 mb-6">Sign up to continue</p>

          <form @submit.prevent="onSubmit" class="space-y-4">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
              <div>
                <label for="name" class="block text-sm font-medium text-slate-700 mb-1">Name</label>
                <input
                  id="name"
                  v-model="form.name"
                  required
                  class="w-full border border-slate-200 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-400"
                />
              </div>

              <div>
                <label for="lastname" class="block text-sm font-medium text-slate-700 mb-1"
                  >Last Name</label
                >
                <input
                  id="lastname"
                  v-model="form.lastname"
                  required
                  class="w-full border border-slate-200 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-400"
                />
              </div>
            </div>

            <div>
              <label for="email" class="block text-sm font-medium text-slate-700 mb-1">Email</label>
              <input
                id="email"
                v-model="form.email"
                required
                class="w-full border border-slate-200 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-400"
              />
            </div>

            <div>
              <label for="password" class="block text-sm font-medium text-slate-700 mb-1"
                >Password</label
              >

              <div class="relative">
                <input
                  :type="showPassword ? 'text' : 'password'"
                  id="password"
                  v-model="form.password"
                  required
                  class="w-full pr-10 border border-slate-200 rounded-md px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-400"
                />

                <button
                  type="button"
                  @click="showPassword = !showPassword"
                  :aria-label="showPassword ? 'Ocultar contraseña' : 'Mostrar contraseña'"
                  class="absolute inset-y-0 right-2 flex items-center text-slate-500 hover:text-slate-700 focus:outline-none focus:ring-2 focus:ring-sky-400 rounded px-2"
                >
                  <!-- Icon: ojo (mostrar) -->
                  <svg
                    v-if="!showPassword"
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5"
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"
                    />
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M2.458 12C3.732 7.943 7.523 5 12 5c4.477 0 8.268 2.943 9.542 7-1.274 4.057-5.065 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"
                    />
                  </svg>

                  <!-- Icon: ojo tachado (ocultar) -->
                  <svg
                    v-else
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5"
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M13.875 18.825A10.05 10.05 0 0112 19c-4.477 0-8.268-2.943-9.542-7a10.05 10.05 0 012.184-3.375M3 3l18 18"
                    />
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M9.88 9.88A3 3 0 1114.12 14.12"
                    />
                  </svg>
                </button>
              </div>
            </div>

            <div>
              <!-- TASK: @click will remove when I finish the validation for inputs -->
              <button
                type="submit"
                class="w-full bg-sky-600 hover:bg-sky-500 text-white py-2 rounded-md font-semibold"
                @click="$router.push('/login')"
              >
                Sign Up
              </button>
            </div>
          </form>

          <p class="mt-4 text-sm text-slate-500">
            Already have an account?
            <router-link to="/login" class="text-sky-600 hover:underline">Login now</router-link>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import NavbarContent from '../components/ui/NavbarContent.vue'
import { reactive, ref } from 'vue'

// TASK: Uncomment when ready to use router for redirection
// import { useRouter } from 'vue-router'

// const router = useRouter()
const showPassword = ref(false)
const form = reactive({ username: '', password: '', remember: false })

// function onSubmit() {
//   // TODO: replace with real authentication call
//   console.log('Submitting login', { ...form })
//   // Redirect after successful login (placeholder)
//   router.push('/')
// }
//
</script>
