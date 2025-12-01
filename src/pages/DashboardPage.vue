<template>
  <AppShell>
    <template #default>
      <section class="space-y-8">
        <header class="space-y-1">
          <h1 class="text-2xl font-bold text-gray-800">Dashboard Overview</h1>
          <p class="text-sm text-gray-600">Key metrics and recent workshop activity.</p>
        </header>
        <!-- Stats Grid -->
        <div class="grid gap-4 sm:grid-cols-2 xl:grid-cols-4">
          <StatCard
            title="Pending Appointments"
            :value="stats.pendingAppointments"
            subtitle="Awaiting confirmation"
          >
            <template #icon>
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
                  d="M8 7V3m8 4V3M3 11h18M5 21h14a2 2 0 002-2V7H3v12a2 2 0 002 2z"
                />
              </svg>
            </template>
          </StatCard>
          <StatCard
            title="Active Tickets"
            :value="stats.activeTickets"
            subtitle="Currently in progress"
            iconBg="bg-orange-100 text-orange-600"
          >
            <template #icon>
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
                  d="M3 9h4l2-6h6l2 6h4M4 9v12h16V9M9 13h6"
                />
              </svg>
            </template>
          </StatCard>
          <StatCard
            title="Today Revenue"
            :value="formatCurrency(stats.todayRevenue)"
            subtitle="Gross sales"
            iconBg="bg-green-100 text-green-600"
          >
            <template #icon>
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
                  d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.105 0 2-.672 2-1.5S13.105 5 12 5s-2 .672-2 1.5S10.895 8 12 8zm0 8v2m0-14V2"
                />
              </svg>
            </template>
          </StatCard>
          <StatCard
            title="Avg. Repair Time"
            :value="stats.avgRepairTime + ' hrs'"
            subtitle="Last 7 days"
            iconBg="bg-purple-100 text-purple-600"
          >
            <template #icon>
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
                  d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
            </template>
          </StatCard>
        </div>
        <!-- Activity & Quick Actions -->
        <div class="grid gap-6 lg:grid-cols-3">
          <div class="lg:col-span-2 space-y-4">
            <div class="flex items-center justify-between">
              <h2 class="text-lg font-semibold text-gray-800">Recent Activity</h2>
              <button
                class="text-xs font-medium text-sky-600 hover:underline"
                @click="refreshActivity"
              >
                Refresh
              </button>
            </div>
            <ul class="space-y-2">
              <li
                v-for="evt in activity"
                :key="evt.id"
                class="bg-white border border-gray-200 rounded-lg p-3 flex items-center gap-3"
              >
                <div
                  class="h-8 w-8 rounded-md flex items-center justify-center text-sky-600 bg-sky-50"
                  v-html="evt.icon"
                ></div>
                <div class="flex-1">
                  <p class="text-sm font-medium text-gray-700">{{ evt.message }}</p>
                  <p class="text-xs text-gray-500">{{ evt.time }}</p>
                </div>
                <span
                  class="text-[10px] px-2 py-0.5 rounded-full bg-gray-100 text-gray-600 font-semibold uppercase"
                  >{{ evt.type }}</span
                >
              </li>
            </ul>
          </div>
          <div class="space-y-4">
            <h2 class="text-lg font-semibold text-gray-800">Quick Actions</h2>
            <div class="grid gap-3">
              <button @click="go('/appointments')" class="quick-btn">Schedule Appointment</button>
              <button @click="go('/tickets')" class="quick-btn">Create Service Ticket</button>
              <button @click="go('/customers')" class="quick-btn">Add New Customer</button>
              <button @click="go('/inventory')" class="quick-btn">Update Inventory</button>
            </div>
          </div>
        </div>
      </section>
    </template>
  </AppShell>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import AppShell from '@/components/admin/AppShell.vue'
import StatCard from '@/components/admin/StatCard.vue'

const router = useRouter()
function go(path) {
  router.push(path)
}

const stats = ref({
  pendingAppointments: 12,
  activeTickets: 7,
  todayRevenue: 2450.75,
  avgRepairTime: 5.4,
})

function formatCurrency(amount) {
  return new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD' }).format(amount)
}

const activity = ref([
  {
    id: 1,
    type: 'APPT',
    message: 'New appointment booked for Ford F-150',
    time: '2m ago',
    icon: icon('calendar'),
  },
  {
    id: 2,
    type: 'TICKET',
    message: 'Ticket #432 updated: Brake Service',
    time: '10m ago',
    icon: icon('ticket'),
  },
  {
    id: 3,
    type: 'PAY',
    message: 'Payment received: Invoice #982',
    time: '25m ago',
    icon: icon('credit-card'),
  },
  { id: 4, type: 'INV', message: 'Low stock alert: Oil Filter', time: '1h ago', icon: icon('box') },
])

function refreshActivity() {
  // Simulate refresh
  activity.value.unshift({
    id: Date.now(),
    type: 'SYS',
    message: 'Dashboard data refreshed',
    time: 'Just now',
    icon: icon('gauge'),
  })
}

function icon(name) {
  const map = {
    calendar:
      '<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3M3 11h18M5 21h14a2 2 0 002-2V7H3v12a2 2 0 002 2z" /></svg>',
    ticket:
      '<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9h4l2-6h6l2 6h4M4 9v12h16V9M9 13h6" /></svg>',
    'credit-card':
      '<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2 7h20v10H2V7zm0 4h20M6 15h3" /></svg>',
    box: '<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 7l9-4 9 4-9 4-9-4v10l9 4 9-4V11" /></svg>',
    gauge:
      '<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3a9 9 0 100 18 9 9 0 000-18zm0 9l3.5 3.5" /></svg>',
  }
  return map[name] || ''
}
</script>

<style scoped>
.quick-btn {
  @apply w-full text-left px-4 py-2 rounded-lg bg-white border border-gray-200 text-sm font-medium hover:border-sky-400 hover:shadow-sm transition;
}
</style>
