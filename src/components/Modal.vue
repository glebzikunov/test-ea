<script setup>
import { ref, defineProps, defineEmits } from "vue"

const props = defineProps({
  show: Boolean,
  title: String,
  subtitle: String,
})

const emit = defineEmits(["close"])

const closeModal = () => {
  emit("close")
}
</script>

<template>
  <aside class="modal" v-show="show">
    <div class="modal__content">
      <img
        src="../assets/close-modal.svg"
        alt="Close modal"
        class="close-modal__img"
        @click="closeModal"
      />
      <h3 class="modal__title">{{ title }}</h3>
      <p class="modal__subtitle">
        {{ subtitle }}
      </p>
      <button class="close-modal__btn" @click="closeModal">Close</button>
    </div>
  </aside>
</template>

<style lang="scss" scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 20;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgba(22, 44, 78, 0.6);
  padding: 0px 20px;
}

.modal__content {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 320px;
  width: 100%;
  height: 370px;
  background-color: #ffffff;

  img {
    position: absolute;
    top: 24px;
    right: 16px;
    cursor: pointer;
    transition: 0.15s;
  }

  img:hover {
    transform: rotate(90deg);
  }
}

.modal__title {
  margin-top: 97px;
  font-weight: 700;
  font-size: 36px;
  line-height: 104%;
  text-align: center;
  text-transform: uppercase;
  color: #162c4e;
}

.modal__subtitle {
  max-width: 280px;
  width: 100%;
  margin-top: 29px;
  font-size: 16px;
  line-height: 150%;
  text-align: center;
  color: rgba(0, 0, 0, 0.8);
}

.close-modal__btn {
  margin-top: 30px;
  background-color: #162c4e;
  border-radius: 40px;
  padding: 16px 73px 16.68px 74px;
  font-size: 18px;
  line-height: 150%;
  color: #ffffff;
  cursor: pointer;
  transition: 0.15s;
}

.close-modal__btn:hover {
  opacity: 0.9;
}

.close-modal__btn:active {
  opacity: 0.8;
}
</style>
