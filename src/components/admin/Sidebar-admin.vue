<template>
  <aside
    :class="[
      'fixed top-0 left-0 bottom-0 z-30 bg-[#1E2A4A] text-gray-200 transition-all duration-200 flex flex-col pt-14 shadow-lg',
      collapsed ? 'w-16' : 'w-64',
    ]"
    role="navigation"
    aria-label="Main sidebar"
  >
    <nav class="flex-1 overflow-y-auto px-2 space-y-1">
      <SidebarItem v-for="item in items" :key="item.path" :item="item" :collapsed="collapsed" />
    </nav>
  </aside>
</template>
<script setup>
import { computed, defineComponent, h } from 'vue'
import { RouterLink, useRoute } from 'vue-router'

const items = computed(() => [
  { label: 'Dashboard', icon: 'gauge', path: '/dashboard' },
  { label: 'Service Tickets', icon: 'ticket', path: '/tickets' },
  { label: 'Appointments', icon: 'calendar', path: '/appointments' },
  { label: 'Customers', icon: 'users', path: '/customers' },
  { label: 'Vehicles', icon: 'car', path: '/vehicles' },
  { label: 'Inventory', icon: 'box', path: '/inventory' },
  { label: 'Parts Lookup', icon: 'search', path: '/parts' },
  { label: 'Payments', icon: 'credit-card', path: '/payments' },
  { label: 'Settings', icon: 'settings', path: '/settings' },
])

function iconSvg(name) {
  switch (name) {
    case 'gauge':
      return '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3a9 9 0 100 18 9 9 0 000-18zm0 9l3.5 3.5" />'
    case 'ticket':
      return '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9h4l2-6h6l2 6h4M4 9v12h16V9M9 13h6" />'
    case 'calendar':
      return '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3M3 11h18M5 21h14a2 2 0 002-2V7H3v12a2 2 0 002 2z" />'
    case 'users':
      return '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20v-2a4 4 0 00-4-4H7a4 4 0 00-4 4v2m14-9a4 4 0 10-8 0 4 4 0 008 0zM23 20v-2a4 4 0 00-3-3.87" />'
    case 'car':
      return '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 13l2-5h14l2 5M5 13h14M7 21h2m6 0h2M7 17h.01M17 17h.01" />'
    case 'box':
      return '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 7l9-4 9 4-9 4-9-4v10l9 4 9-4V11" />'
    case 'search':
      return '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-4.35-4.35M11 19a8 8 0 100-16 8 8 0 000 16z" />'
    case 'credit-card':
      return '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2 7h20v10H2V7zm0 4h20M6 15h3" />'
    case 'settings':
      return '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15a3 3 0 100-6 3 3 0 000 6zm7.94-4a7.94 7.94 0 000-2l2.12-1.65a.5.5 0 00.12-.64l-2-3.46a.5.5 0 00-.6-.22l-2.5 1a8 8 0 00-1.73-1l-.38-2.65A.5.5 0 0012.5 0h-4a.5.5 0 00-.5.42L7.62 3.07a8 8 0 00-1.73 1l-2.5-1a.5.5 0 00-.6.22l-2 3.46a.5.5 0 00.12.64L3.06 9a7.94 7.94 0 000 2l-2.12 1.65a.5.5 0 00-.12.64l2 3.46a.5.5 0 00.6.22l2.5-1c.53.42 1.11.78 1.73 1l.38 2.65a.5.5 0 00.5.42h4a.5.5 0 00.5-.42l.38-2.65c.62-.22 1.2-.58 1.73-1l2.5 1a.5.5 0 00.6-.22l2-3.46a.5.5 0 00-.12-.64L19.94 11z" />'
    default:
      return ''
  }
}

const SidebarItem = defineComponent({
  name: 'SidebarItem',
  props: { item: Object, collapsed: Boolean },
  setup(props) {
    const route = useRoute()
    const active = computed(() => route.path === props.item.path)
    return () =>
      h(
        RouterLink,
        {
          to: props.item.path,
          'aria-current': active.value ? 'page' : undefined,
          class: [
            'group flex items-center gap-3 rounded-md px-3 py-2 text-sm font-medium transition outline-none focus:ring-2 focus:ring-sky-500',
            active.value
              ? 'bg-sky-600 text-white'
              : 'text-gray-300 hover:bg-[#243457] hover:text-white',
          ],
        },
        {
          default: () => [
            h('div', {
              innerHTML:
                '<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">' +
                iconSvg(props.item.icon) +
                '</svg>',
            }),
            !props.collapsed && h('span', {}, props.item.label),
          ],
        },
      )
  },
})
</script>
