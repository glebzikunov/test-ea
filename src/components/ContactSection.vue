<script setup>
import ContactForm from "./ContactForm.vue"
</script>

<template>
  <section class="contact-section">
    <div class="contact-section__container">
      <ContactForm />
      <a class="event-link" href="#events">
        <span>Other Events</span>
        <img src="../assets/arrow-right.svg" alt="Arrow down" />
      </a>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.contact-section {
  margin-top: 156px;
  background-color: #162c4e;
}

.contact-section__container {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 190px;
}

.event-link {
  font-size: 20px;
  line-height: 150%;
  color: #ffffff;
  position: absolute;
  right: 108px;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  align-items: center;
  gap: 10px;
  transition: 0.15s;

  img {
    transition: 0.3s;
  }
}

.event-link:hover {
  text-decoration: underline;
  text-underline-offset: 3px;

  img {
    transform: rotate(270deg);
  }
}

@media (max-width: 1024px) {
  .event-link {
    position: relative;
    right: 0;
    top: 0;
    transform: none;

    img {
      transform: rotate(90deg);
    }
  }

  .contact-section__container {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    row-gap: 15px;
    height: 190px;
  }
}

@media (max-width: 768px) {
  .event-link {
    gap: 3px;
    font-size: 16px;
  }
}

@media (max-width: 360px) {
  .event-link {
    gap: 4px;
  }
}
</style>
