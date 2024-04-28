<script setup>
import Accordion from "./Accordion.vue"
</script>

<template>
  <section class="events-section">
    <div class="events-section__container">
      <h1 id="events" class="events-section__title">All Events</h1>
      <Accordion />
    </div>
  </section>
</template>

<style scoped>
.events-section {
  padding: 110px 0px 99px 0px;
}

.events-section__container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 40px;
}

.events-section__title {
  font-weight: 700;
  font-size: 72px;
  line-height: 104%;
  text-transform: uppercase;
  color: #162c4e;
  opacity: 0.39;
  text-align: center;
}
</style>
