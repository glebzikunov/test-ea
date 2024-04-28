<script setup>
import { ref } from "vue"
import { tabs } from "../constants/index.js"
const openTab = ref(0)

const toggleTab = (index) => {
  openTab.value = index
}
</script>

<template>
  <div class="events__accordion">
    <ul class="accordion">
      <li
        class="accordion__item"
        v-for="(item, index) in tabs"
        :key="index"
        @click="toggleTab(index)"
        :class="{ active: openTab === index }"
        :style="{ 'background-image': `url(${item.image})` }"
      >
        <div class="events__heading">
          <span class="heading__number">{{ item.number }}</span>
          <span class="vertical">{{ item.heading }}</span>
        </div>
        <div class="events__content">
          <h3 class="content__title">{{ item.heading }}</h3>
          <p class="content__datetime">{{ item.date }}</p>
          <a
            class="content__link"
            href="https://leadentrepreneursummit.com/"
            target="_blank"
            >More information</a
          >
        </div>
        <div class="left__number">{{ item.number }}</div>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.events__accordion {
  width: 100%;
}

.accordion {
  display: flex;
  gap: 4px;
  height: 682px;

  .accordion__item {
    position: relative;
    border-bottom: 3px solid #df2224;
    background: no-repeat center / cover;
    background-position-y: 10%;

    width: 100%;
    display: flex;
    list-style: none;
    position: relative;
    transition: 0.3s ease-in;
    overflow: hidden;
    max-width: 85px;
    z-index: 1;
  }

  .accordion__item:nth-of-type(2) {
    background-position-y: 80%;
  }

  .accordion__item.active {
    max-width: 1082px;

    .events__heading {
      background-color: #162c4e;
      top: 0px;
      transition: none;
    }
  }
}
.events__heading {
  font-family: "SF Pro Display";
  position: relative;
  background-image: none;
  background-position-x: 50%;
  background-position-y: 50%;
  background-size: cover;
  background: linear-gradient(180deg, rgba(22, 44, 78, 0.3) 0%, #162c4e 70%);

  display: flex;
  flex-direction: column-reverse;
  align-items: center;
  padding-bottom: 20px;
  height: 682px;
  width: 85px;
  cursor: pointer;

  backdrop-filter: grayscale(100%);
  -webkit-user-select: none;
  -ms-user-select: none;
  user-select: none;
  z-index: 2;
  transition: 1.5s;
}

.heading__number {
  margin-top: 40px;
  font-size: 40px;
  font-weight: 500;
  color: #ffffff;
}

.vertical {
  display: flex;
  font-style: normal;
  font-weight: 600;
  font-size: 32px;
  color: #ffffff;
  writing-mode: tb-rl;
  transform: rotate(180deg);
}

.left__number {
  position: absolute;
  width: 450px;
  height: 380px;
  left: -57px;
  top: -38px;
  font-weight: 600;
  font-size: 380px;
  line-height: 100%;
  letter-spacing: -0.03em;
  color: rgba(255, 255, 255, 0.04);
}

.events__content {
  display: flex;
  flex-direction: column;
  justify-content: end;
  background-color: rgba(18, 18, 18, 0.6);
  backdrop-filter: blur(20px);
  max-width: 364px;
  width: 100%;
  height: 100%;
  position: absolute;
  padding: 0px 0px 50px 42px;
  left: 85px;
  top: 0;
}

.content__title {
  font-size: 24px;
  font-weight: 600;
  color: #ffffff;
}

.content__datetime {
  margin-top: 12px;
  font-size: 18px;
  color: rgba(255, 255, 255, 0.8);
}

.content__link {
  display: flex;
  align-items: center;
  justify-content: center;
  max-width: 256px;
  margin-top: 25px;
  border: 1px solid;
  border-left-width: 6px;
  color: #ffffff;
  padding: 20px 26px;
  transition: 0.15s;
}

.content__link:hover {
  border-left-width: 20px;
  padding: 20px 26px 20px 20px;
}
</style>
