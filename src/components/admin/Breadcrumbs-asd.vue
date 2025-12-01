<template>
  <nav class="text-xs font-medium text-gray-500" aria-label="Breadcrumb">
    <ol class="flex items-center gap-1 flex-wrap">
      <li>
        <RouterLink to="/dashboard" class="hover:text-sky-600">Dashboard</RouterLink>
      </li>
      <li v-for="(seg, i) in crumbs" :key="i" class="flex items-center gap-1">
        <span>/</span>
        <RouterLink :to="seg.to" class="hover:text-sky-600">{{ seg.label }}</RouterLink>
      </li>
    </ol>
  </nav>
</template>
<script setup>
import { computed } from 'vue'
import { useRoute, RouterLink } from 'vue-router'
const route = useRoute()
const mapLabel = (part) => {
  const mapping = {
    dashboard: 'Dashboard',
    tickets: 'Service Tickets',
    appointments: 'Appointments',
    customers: 'Customers',
    vehicles: 'Vehicles',
    inventory: 'Inventory',
    parts: 'Parts Lookup',
    payments: 'Payments',
    settings: 'Settings',
  }
  return mapping[part] || part
}
const crumbs = computed(() => {
  if (route.path === '/dashboard') return []
  const parts = route.path.split('/').filter(Boolean)
  return parts.map((p, idx) => ({
    label: mapLabel(p),
    to: '/' + parts.slice(0, idx + 1).join('/'),
  }))
})
</script>
