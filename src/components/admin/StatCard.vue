<template>
  <div class="rounded-xl bg-white border border-gray-200 shadow-sm p-4 flex flex-col gap-2">
    <div class="flex items-center justify-between">
      <h3 class="text-sm font-semibold text-gray-700">{{ title }}</h3>
      <div class="h-8 w-8 flex items-center justify-center rounded-lg" :class="iconBg">
        <slot name="icon" />
      </div>
    </div>
    <div class="text-2xl font-bold text-gray-800">{{ value }}</div>
    <p class="text-xs text-gray-500">{{ subtitle }}</p>
  </div>
</template>
<script setup>
const props = defineProps({
  title: String,
  value: [String, Number],
  subtitle: String,
  trend: String,
  iconBg: { type: String, default: 'bg-sky-100 text-sky-600' },
})
</script>
