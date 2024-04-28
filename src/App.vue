<script setup>
import AppHeader from "./components/AppHeader.vue"
import ContactSection from "./components/ContactSection.vue"
import UnderConstruction from "./components/UnderConstruction.vue"
import Events from "./components/Events.vue"
</script>

<template>
  <div class="wrapper">
    <AppHeader />
    <main>
      <UnderConstruction />
      <ContactSection />
      <Events />
    </main>
  </div>
</template>
