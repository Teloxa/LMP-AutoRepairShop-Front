<template>
  <NavbarContent />
  <div class="container mx-auto px-4 py-8">
    <AppointmentForm />
  </div>
</template>

<script>
import NavbarContent from '@/components/ui/NavbarContent.vue'
import AppointmentForm from '@/components/vehicles/AppointmentForm.vue'
export default {
  components: { NavbarContent, AppointmentForm },
}
</script>
