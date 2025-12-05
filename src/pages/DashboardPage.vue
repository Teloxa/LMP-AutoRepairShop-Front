<template>
  <h1>You're on dashboard page</h1>
  <SideBar />
  <Navbar />
</template>

<script>
import SideBar from '@/components/admin/Sidebar.vue'
import Navbar from '@/components/admin/Navbar.vue'

export default {
  components: {
    SideBar,
    Navbar,
  },
}
</script>
