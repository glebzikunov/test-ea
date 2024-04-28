<script setup>
import { ref } from "vue"
import Modal from "./Modal.vue"
import emailjs from "@emailjs/browser"

const showModal = ref(false)
const modalTitle = ref("Success!")
const modalSubtitle = ref(
  "You have successfully subscribed to the email newsletter"
)
const form = ref(null)
const emailInput = ref("")

const submitForm = () => {
  if (!/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(emailInput.value)) {
    alert("Enter valid Email address!")
    return
  }

  emailjs
    .sendForm(
      import.meta.env.VITE_EMAIL_SERVICE_ID,
      import.meta.env.VITE_EMAIL_TEMPLATE_ID,
      form.value,
      {
        publicKey: import.meta.env.VITE_EMAIL_PUBLIC_KEY,
      }
    )
    .then((response) => {
      console.log("Email sent:", response)
      showModal.value = true
      emailInput.value = ""
    })
    .catch((error) => {
      console.error("Error sending email:", error)
      modalTitle.value = "Error!"
      modalSubtitle.value = "There was an error with your subscription."
      emailInput.value = ""
      showModal.value = true
    })
}
</script>

<template>
  <form
    ref="form"
    class="contact-section__form form"
    @submit.prevent="submitForm"
  >
    <div class="form-input__wrapper">
      <input
        v-model="emailInput"
        class="form-input"
        type="email"
        name="user_email"
        placeholder="Enter your Email and get notified"
        required
      />
      <button class="form-button" type="submit">
        <img src="../assets/arrow-right.svg" alt="Arrow to right" />
      </button>
    </div>
  </form>
  <Modal
    :show="showModal"
    :title="modalTitle"
    :subtitle="modalSubtitle"
    @close="showModal = false"
  />
</template>

<style lang="scss" scoped>
.form {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.form-input__wrapper {
  display: flex;
  max-width: 440px;
  width: 100%;
  background-color: #ffffff;
  padding: 16px 8px 16px 27px;
  border-radius: 40px;
  justify-content: space-between;

  .form-input {
    max-width: 259px;
    width: 100%;
    font-family: "Roboto";
    font-weight: 400;
    font-size: 18px;
    line-height: 150%;
  }

  .form-input:focus {
    outline: none;
  }
}

.form-button {
  width: 42px;
  height: 42px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background-color: #df2224;
  cursor: pointer;
  transition: 0.3s;
}

.form-button:hover {
  opacity: 0.85;
  transform: rotate(270deg);
}

@media (max-width: 768px) {
  .form-input__wrapper {
    max-width: 360px;
    padding: 10px 8px 10px 20px;

    .form-input {
      max-width: 202px;
      width: 100%;
      font-size: 14px;
    }
  }

  .form-button {
    width: 33px;
    height: 33px;
  }
}

@media (max-width: 360px) {
  .form-input__wrapper {
    width: 280px;
  }
}
</style>
