<template>
  <div
    class="bg-white shadow-lg hover:shadow-xl transition duration-300 border border-gray-100 flex flex-col h-full rounded-t-xl overflow-hidden"
  >
    <!-- Full-width image at the top with rounded top corners only -->
    <img
      :src="imagePlaceholder"
      :alt="'Image for ' + title"
      class="w-full h-44 md:h-56 lg:h-48 object-cover"
    />

    <div class="p-6 flex flex-col flex-grow">
      <!-- Título -->
      <h3 class="text-xl font-semibold text-gray-800 mb-3">{{ title }}</h3>

      <!-- Descripción -->
      <p class="text-gray-600 mb-6 flex-grow">{{ description }}</p>

      <!-- Botón de Acción -->
      <button
        class="w-full mt-auto py-2 text-sm font-medium border border-sky-600 text-sky-600 rounded-lg hover:bg-sky-50 transition duration-200"
        @click="handleReadMore"
      >
        More Details
      </button>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
  imagePlaceholder: {
    type: String,
    required: true,
  },
})

const handleReadMore = () => {
  // Aquí puedes implementar una lógica para navegar a una página de detalles del servicio
  alert(`Navegando a la página de detalles de: ${props.title}`)
  // Usarías router.push() en una aplicación real
}
</script>
