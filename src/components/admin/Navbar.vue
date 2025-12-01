<template>
  <header
    class="fixed top-0 left-0 right-0 h-14 flex items-center px-4 bg-[#1E2A4A] text-white z-40 shadow"
  >
    <div class="flex items-center gap-2 font-semibold text-sm">
      <button class="md:hidden p-1 rounded hover:bg-white/10" @click="$emit('toggleSidebar')">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16M4 18h16"
          />
        </svg>
      </button>
      <span class="text-lg">🔧 AutoWorkshop</span>
    </div>
    <div class="flex-1 flex justify-center">
      <div class="w-full max-w-md relative">
        <input
          v-model="search"
          type="text"
          placeholder="Search anything..."
          class="w-full rounded-lg bg-[#243457] border border-[#2f4570] px-3 py-1.5 text-sm placeholder-gray-300 focus:outline-none focus:ring-2 focus:ring-sky-500"
        />
        <svg
          class="absolute right-3 top-2.5 h-5 w-5 text-gray-300"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M21 21l-4.35-4.35M11 19a8 8 0 100-16 8 8 0 000 16z"
          />
        </svg>
      </div>
    </div>
    <div class="flex items-center gap-4">
      <button class="relative p-2 rounded hover:bg-white/10" @click="notify">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"
          />
        </svg>
        <span
          v-if="notifications"
          class="absolute -top-0.5 -right-0.5 bg-sky-500 text-[10px] font-bold rounded-full px-1"
          >{{ notifications }}</span
        >
      </button>
      <div class="relative" @click="toggleProfile">
        <div class="flex items-center gap-2 cursor-pointer select-none">
          <div
            class="h-8 w-8 rounded-full bg-sky-500 flex items-center justify-center text-sm font-semibold"
          >
            AD
          </div>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-4 w-4"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M19 9l-7 7-7-7"
            />
          </svg>
        </div>
        <div
          v-if="showProfile"
          class="absolute right-0 mt-2 w-48 bg-white text-gray-800 rounded-lg shadow border border-gray-200 py-2 text-sm"
        >
          <button class="w-full text-left px-3 py-1.5 hover:bg-gray-100">Profile</button>
          <button class="w-full text-left px-3 py-1.5 hover:bg-gray-100">Settings</button>
          <div class="border-t my-1"></div>
          <button class="w-full text-left px-3 py-1.5 hover:bg-gray-100 text-red-600">
            Logout
          </button>
        </div>
      </div>
    </div>
  </header>
</template>
<script setup>
import { ref } from 'vue'
const search = ref('')
const notifications = ref(3)
const showProfile = ref(false)
function toggleProfile() {
  showProfile.value = !showProfile.value
}
function notify() {
  notifications.value = Math.max(0, notifications.value - 1)
}
</script>
