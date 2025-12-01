<template>
  <div class="min-h-screen flex flex-col bg-[#F0F2F5] text-gray-800">
    <Navbar @toggleSidebar="toggleSidebar" />
    <div class="flex flex-1 overflow-hidden">
      <Sidebar :collapsed="sidebarCollapsed" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Navbar from './Navbar-admin.vue'
import Sidebar from './Sidebar-admin.vue'

const sidebarCollapsed = ref(false)
function toggleSidebar() {
  sidebarCollapsed.value = !sidebarCollapsed.value
}
</script>
