<template>
  <form class="max-w-3xl mx-auto bg-white rounded-xl shadow-lg p-6 space-y-6">
    <h2 class="text-2xl font-bold text-gray-800">Personal Information</h2>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      <div>
        <label class="block text-sm font-medium text-gray-700">First Name *</label>
        <input
          v-model="firstName"
          type="text"
          class="mt-1 w-full rounded-lg border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-500"
        />
        <p v-if="errors.firstName" class="text-red-600 text-xs mt-1">{{ errors.firstName }}</p>
      </div>
      <div>
        <label class="block text-sm font-medium text-gray-700">Last Name *</label>
        <input
          v-model="lastName"
          type="text"
          class="mt-1 w-full rounded-lg border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-500"
        />
        <p v-if="errors.lastName" class="text-red-600 text-xs mt-1">{{ errors.lastName }}</p>
      </div>
      <div>
        <label class="block text-sm font-medium text-gray-700">Phone Number *</label>
        <input
          v-model="phone"
          type="tel"
          placeholder="555-123-4567"
          class="mt-1 w-full rounded-lg border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-500"
        />
        <p v-if="errors.phone" class="text-red-600 text-xs mt-1">{{ errors.phone }}</p>
      </div>
      <div>
        <label class="block text-sm font-medium text-gray-700">Address</label>
        <textarea
          v-model="address"
          rows="2"
          class="mt-1 w-full rounded-lg border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-500"
        ></textarea>
      </div>
    </div>

    <h2 class="text-2xl font-bold text-gray-800">Vehicle Information</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
      <div>
        <label class="block text-sm font-medium text-gray-700">Brand *</label>
        <select
          v-model="selectedBrand"
          class="mt-1 w-full rounded-lg border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-500"
        >
          <option value="">Select Brand</option>
          <option v-for="brand in brands" :key="brand.name" :value="brand.name">
            {{ brand.name }}
          </option>
        </select>
        <p v-if="errors.brand" class="text-red-600 text-xs mt-1">{{ errors.brand }}</p>
      </div>
      <div>
        <label class="block text-sm font-medium text-gray-700">Model *</label>
        <select
          v-model="selectedModel"
          :disabled="!selectedBrand"
          class="mt-1 w-full rounded-lg border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-500 disabled:bg-gray-100 disabled:text-gray-400"
        >
          <option value="">Select Model</option>
          <option v-for="model in modelsForBrand" :key="model" :value="model">{{ model }}</option>
        </select>
        <p v-if="errors.model" class="text-red-600 text-xs mt-1">{{ errors.model }}</p>
      </div>
      <div>
        <label class="block text-sm font-medium text-gray-700">Year *</label>
        <select
          v-model="selectedYear"
          :disabled="!selectedModel"
          class="mt-1 w-full rounded-lg border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-500 disabled:bg-gray-100 disabled:text-gray-400"
        >
          <option value="">Select Year</option>
          <option v-for="yr in yearsForModel" :key="yr" :value="yr">{{ yr }}</option>
        </select>
        <p v-if="errors.year" class="text-red-600 text-xs mt-1">{{ errors.year }}</p>
      </div>
    </div>

    <h2 class="text-2xl font-bold text-gray-800">Service Selection</h2>
    <div class="space-y-2">
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-2">
        <label class="inline-flex items-center gap-2"
          ><input type="checkbox" value="Oil Change" v-model="services" /> Oil Change</label
        >
        <label class="inline-flex items-center gap-2"
          ><input type="checkbox" value="Brake Service" v-model="services" /> Brake Service</label
        >
        <label class="inline-flex items-center gap-2"
          ><input type="checkbox" value="Tire Rotation" v-model="services" /> Tire Rotation</label
        >
        <label class="inline-flex items-center gap-2"
          ><input type="checkbox" value="Engine Repair" v-model="services" /> Engine Repair</label
        >
        <label class="inline-flex items-center gap-2"
          ><input type="checkbox" value="Transmission Service" v-model="services" /> Transmission
          Service</label
        >
        <label class="inline-flex items-center gap-2"
          ><input type="checkbox" value="AC Repair" v-model="services" /> AC Repair</label
        >
        <label class="inline-flex items-center gap-2"
          ><input type="checkbox" value="Electrical Diagnostics" v-model="services" /> Electrical
          Diagnostics</label
        >
        <label class="inline-flex items-center gap-2"
          ><input type="checkbox" value="General Maintenance" v-model="services" /> General
          Maintenance</label
        >
      </div>
      <p v-if="errors.services" class="text-red-600 text-xs mt-1">{{ errors.services }}</p>
    </div>

    <h2 class="text-2xl font-bold text-gray-800">Additional Description</h2>
    <textarea
      v-model="description"
      rows="4"
      placeholder="Please describe any specific issues or special requests..."
      class="w-full rounded-lg border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-sky-500"
    ></textarea>

    <!-- Cost Estimate -->
    <div class="mt-6 border-t pt-4">
      <h3 class="text-xl font-semibold text-gray-800 mb-3">Estimated Cost</h3>
      <div v-if="services.length" class="space-y-2">
        <div v-for="svc in services" :key="svc" class="flex justify-between text-sm">
          <span>{{ svc }}</span>
          <span class="font-medium">{{ formatCurrency(serviceLinePrice(svc)) }}</span>
        </div>
        <div class="flex justify-between text-base font-semibold mt-2">
          <span>Total</span>
          <span>{{ formatCurrency(totalCost) }}</span>
        </div>
        <p class="text-xs text-gray-500 mt-1">
          Prices are estimates and may vary based on diagnostics.
        </p>
      </div>
      <p v-else class="text-sm text-gray-600">Select services to see an estimated total.</p>
    </div>
    <!-- Submit Button -->
    <div class="flex items-center gap-3">
      <button
        :disabled="submitting"
        @click.prevent="onSubmit"
        class="px-6 py-3 rounded-lg text-white font-semibold transition disabled:opacity-50 disabled:cursor-not-allowed bg-sky-600 hover:bg-sky-500"
      >
        <span v-if="!submitting">Book Appointment</span>
        <span v-else>Processing...</span>
      </button>
      <span v-if="submitMessage" class="text-green-700 text-sm">{{ submitMessage }}</span>
    </div>
  </form>
</template>

<script setup>
import { reactive, ref, computed, watch } from 'vue'

const brands = [
  {
    name: 'Toyota',
    models: {
      Corolla: [2015, 2016, 2017, 2018, 2019, 2020, 2021],
      Camry: [2014, 2016, 2018, 2020, 2022],
    },
  },
  { name: 'Ford', models: { Focus: [2012, 2014, 2016, 2018], 'F-150': [2010, 2015, 2018, 2021] } },
  {
    name: 'Honda',
    models: { Civic: [2013, 2015, 2017, 2019, 2021], Accord: [2012, 2016, 2019, 2022] },
  },
  {
    name: 'Chevrolet',
    models: { Malibu: [2011, 2014, 2017, 2020], Silverado: [2010, 2013, 2016, 2019, 2022] },
  },
  {
    name: 'Nissan',
    models: { Sentra: [2012, 2015, 2018, 2021], Altima: [2010, 2013, 2016, 2019] },
  },
  {
    name: 'BMW',
    models: { '3 Series': [2011, 2014, 2017, 2020], '5 Series': [2010, 2013, 2016, 2019] },
  },
  {
    name: 'Mercedes',
    models: { 'C-Class': [2012, 2015, 2018, 2021], 'E-Class': [2010, 2014, 2017, 2020] },
  },
  { name: 'Audi', models: { A4: [2011, 2014, 2017, 2020], A6: [2010, 2013, 2016, 2019] } },
  {
    name: 'Hyundai',
    models: { Elantra: [2012, 2015, 2018, 2021], Sonata: [2010, 2014, 2017, 2020] },
  },
  { name: 'Kia', models: { Forte: [2013, 2016, 2019, 2022], Optima: [2011, 2014, 2017, 2020] } },
]

const firstName = ref('')
const lastName = ref('')
const phone = ref('')
const address = ref('')
const selectedBrand = ref('')
const selectedModel = ref('')
const selectedYear = ref('')
const services = ref([])
const description = ref('')
const submitting = ref(false)
const submitMessage = ref('')

const errors = reactive({
  firstName: '',
  lastName: '',
  phone: '',
  brand: '',
  model: '',
  year: '',
  services: '',
})

const modelsForBrand = computed(() => {
  const brand = brands.find((b) => b.name === selectedBrand.value)
  return brand ? Object.keys(brand.models) : []
})

const yearsForModel = computed(() => {
  const brand = brands.find((b) => b.name === selectedBrand.value)
  if (!brand) return []
  const years = brand.models[selectedModel.value]
  return years || []
})

watch(selectedBrand, () => {
  selectedModel.value = ''
  selectedYear.value = ''
})

watch(selectedModel, () => {
  selectedYear.value = ''
})

function validatePhone(value) {
  const re = /^(\(\d{3}\)\s?|\d{3}[- ]?)\d{3}[- ]?\d{4}$/
  return re.test(String(value))
}

function validateForm() {
  errors.firstName = firstName.value ? '' : 'First name is required.'
  errors.lastName = lastName.value ? '' : 'Last name is required.'
  errors.phone = validatePhone(phone.value) ? '' : 'Valid phone number is required.'
  errors.brand = selectedBrand.value ? '' : 'Brand is required.'
  errors.model = selectedModel.value ? '' : 'Model is required.'
  errors.year = selectedYear.value ? '' : 'Year is required.'
  errors.services = services.value.length ? '' : 'Select at least one service.'
  return Object.values(errors).every((e) => e === '')
}

// Pricing
const servicePrices = reactive({
  'Oil Change': 40,
  'Brake Service': 120,
  'Tire Rotation': 30,
  'Engine Repair': 250,
  'Transmission Service': 300,
  'AC Repair': 180,
  'Electrical Diagnostics': 85,
  'General Maintenance': 99,
})

function serviceLinePrice(svc) {
  return servicePrices[svc] ?? 0
}

const totalCost = computed(() => {
  return services.value.reduce((sum, s) => sum + serviceLinePrice(s), 0)
})

function formatCurrency(amount) {
  return new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD' }).format(
    Number(amount) || 0,
  )
}
async function onSubmit() {
  if (!validateForm()) {
    submitMessage.value = 'Please fix the errors in the form.'
    return
  }
  submitting.value = true
  submitMessage.value = ''
  try {
    // Simulate submission delay
    await new Promise((resolve) => setTimeout(resolve, 800))
    submitMessage.value = 'Appointment request submitted successfully.'
  } catch (e) {
    submitMessage.value = 'An unexpected error occurred. Please try again.'
  } finally {
    submitting.value = false
  }
}
</script>
