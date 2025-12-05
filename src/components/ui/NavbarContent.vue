<template>
  <nav
    class="flex items-center justify-between gap-4 px-4 py-3 bg-gradient-to-r from-slate-900 via-slate-900/95 to-slate-950 text-white shadow-md"
    ref="navRef"
  >
    <div class="flex items-center gap-3">
      <img
        src="@/assets/logo.png"
        alt="Logo"
        class="h-14 object-contain cursor-pointer transition transform duration-150 hover:scale-105 hover:opacity-90 rounded focus:outline-none"
        @click="$router.push('/')"
        tabindex="0"
        @keydown.enter="$router.push('/')"
      />
      <!-- <span class="font-bold text-lg hidden sm:inline">LMP</span> -->
    </div>

    <ul class="flex items-center gap-3">
      <li class="relative">
        <router-link
          to="/"
          class="inline-flex items-center gap-2 px-3 py-2 rounded-md text-slate-100 font-semibold hover:bg-white/5"
          >Home</router-link
        >
      </li>

      <!-- Services dropdown -->
      <li class="relative">
        <button
          class="inline-flex items-center gap-2 px-3 py-2 rounded-md text-slate-100 font-semibold hover:bg-white/5"
          @click.stop="toggleDropdown('services')"
          :aria-expanded="String(openDropdown === 'services')"
        >
          Services
          <span
            :class="[
              'ml-2 transform transition-transform duration-150',
              { 'rotate-180': openDropdown === 'services' },
            ]"
            >▾</span
          >
        </button>

        <transition
          enter-active-class="transition ease-out duration-150"
          enter-from-class="opacity-0 translate-y-1"
          enter-to-class="opacity-100 translate-y-0"
          leave-active-class="transition ease-in duration-100"
          leave-from-class="opacity-100 translate-y-0"
          leave-to-class="opacity-0 translate-y-1"
        >
          <ul
            v-show="openDropdown === 'services'"
            class="absolute top-full mt-2 left-0 min-w-[160px] bg-slate-800 border border-white/5 rounded-md py-1 shadow-lg z-40"
          >
            <li>
              <router-link
                to="/services/one"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >Brakes</router-link
              >
            </li>
            <li>
              <router-link
                to="/services/one"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >Oil Change</router-link
              >
            </li>
            <li>
              <router-link
                to="/services/two"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >Tune Up</router-link
              >
            </li>
            <li>
              <router-link
                to="/services/three"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >General Maintenance</router-link
              >
            </li>
          </ul>
        </transition>
      </li>

      <!-- Products dropdown (new) -->
      <li class="relative">
        <button
          class="inline-flex items-center gap-2 px-3 py-2 rounded-md text-slate-100 font-semibold hover:bg-white/5"
          @click.stop="toggleDropdown('products')"
          :aria-expanded="String(openDropdown === 'products')"
        >
          Products
          <span
            :class="[
              'ml-2 transform transition-transform duration-150',
              { 'rotate-180': openDropdown === 'products' },
            ]"
            >▾</span
          >
        </button>

        <transition
          enter-active-class="transition ease-out duration-150"
          enter-from-class="opacity-0 translate-y-1"
          enter-to-class="opacity-100 translate-y-0"
          leave-active-class="transition ease-in duration-100"
          leave-from-class="opacity-100 translate-y-0"
          leave-to-class="opacity-0 translate-y-1"
        >
          <ul
            v-show="openDropdown === 'products'"
            class="absolute top-full mt-2 left-0 min-w-[160px] bg-slate-800 border border-white/5 rounded-md py-1 shadow-lg z-40"
          >
            <li>
              <router-link
                to="/products/parts"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >Performance Parts</router-link
              >
            </li>
            <li>
              <router-link
                to="/products/tools"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >Brake Pads & Rotors</router-link
              >
            </li>
            <li>
              <router-link
                to="/products/tools"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >Batteries</router-link
              >
            </li>
            <li>
              <router-link
                to="/products/tools"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >Tires & Wheels</router-link
              >
            </li>
            <li>
              <router-link
                to="/products/tools"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >Oil & Fluids</router-link
              >
            </li>
          </ul>
        </transition>
      </li>

      <!-- Customer Resources dropdown (new) -->
      <li class="relative">
        <button
          class="inline-flex items-center gap-2 px-3 py-2 rounded-md text-slate-100 font-semibold hover:bg-white/5"
          @click.stop="toggleDropdown('customer-resources')"
          :aria-expanded="String(openDropdown === 'customer-resources')"
        >
          Customer Resources
          <span
            :class="[
              'ml-2 transform transition-transform duration-150',
              { 'rotate-180': openDropdown === 'customer-resources' },
            ]"
            >▾</span
          >
        </button>

        <transition
          enter-active-class="transition ease-out duration-150"
          enter-from-class="opacity-0 translate-y-1"
          enter-to-class="opacity-100 translate-y-0"
          leave-active-class="transition ease-in duration-100"
          leave-from-class="opacity-100 translate-y-0"
          leave-to-class="opacity-0 translate-y-1"
        >
          <ul
            v-show="openDropdown === 'customer-resources'"
            class="absolute top-full mt-2 left-0 min-w-[160px] bg-slate-800 border border-white/5 rounded-md py-1 shadow-lg z-40"
          >
            <li>
              <router-link
                to="/customer-resources/docs"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >Service Tips</router-link
              >
            </li>
            <li>
              <router-link
                to="/customer-resources/guides"
                class="block px-4 py-2 text-sky-100 font-medium hover:bg-white/5"
                >FAQ</router-link
              >
            </li>
          </ul>
        </transition>
      </li>

      <!-- Simple link without dropdown -->
      <li class="relative">
        <router-link
          to="/about"
          class="inline-flex items-center gap-2 px-3 py-2 rounded-md text-slate-100 font-semibold hover:bg-white/5"
          >About</router-link
        >
      </li>
    </ul>

    <button
      class="bg-white text-sky-700 border font-bold border-sky-600 px-4 py-2 rounded-md"
      @click="$router.push('/login')"
    >
      Log In
    </button>
  </nav>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const openDropdown = ref(null)
const navRef = ref(null)

function toggleDropdown(id) {
  openDropdown.value = openDropdown.value === id ? null : id
}

function onClickOutside(e) {
  if (!navRef.value) return
  if (!navRef.value.contains(e.target)) {
    openDropdown.value = null
  }
}

onMounted(() => {
  document.addEventListener('click', onClickOutside)
})

onBeforeUnmount(() => {
  document.removeEventListener('click', onClickOutside)
})
</script>
