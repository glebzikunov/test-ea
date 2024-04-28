<script setup>
import CountdownTimer from "./CountdownTimer.vue"
import { endDateObject } from "../constants/index.js"
</script>

<template>
  <section class="under-construction">
    <div class="under-construction__container">
      <div class="under-construction__header">
        <h1 class="under-construction__title">Under Construction</h1>
        <p class="under-construction__subtitle">
          We're making lots of improvements and will be back soon
        </p>
      </div>
      <CountdownTimer :endDateObject="{ ...endDateObject }" />
      <div class="event-block">
        <h3 class="event-block__title">Check our event page when you wait:</h3>
        <a
          class="event-link"
          href="https://leadentrepreneursummit.com/"
          target="_blank"
        >
          <span>Go to the event</span>
          <img src="../assets/arrow-right.svg" alt="Arrow to right" />
        </a>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.under-construction {
  margin-top: 93px;
}

.under-construction__container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.under-construction__header {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 8px;
}

.under-construction__title {
  font-weight: 700;
  font-size: 72px;
  line-height: 104%;
  text-transform: uppercase;
  color: #162c4e;
  opacity: 0.39;
  text-align: center;
}

.under-construction__subtitle {
  width: 423px;
  height: 54px;
  font-weight: 400;
  font-size: 18px;
  line-height: 150%;
  text-align: center;
  color: rgba(0, 0, 0, 0.8);
}

.event-block {
  margin-top: 70.82px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.event-block__title {
  font-weight: 400;
  font-size: 18px;
  line-height: 150%;
  color: rgba(0, 0, 0, 0.8);
}

.event-link {
  background-color: #1d4169;
  border-radius: 40px;
  color: #ffffff;
  display: flex;
  padding: 16px 20px 17px 28px;
  margin-top: 12px;
  font-size: 18px;
  line-height: 150%;
  cursor: pointer;
  transition: 0.15s;

  span {
    width: 171px;
  }

  img {
    transition: 0.15s;
  }
}

.event-link:hover {
  opacity: 0.9;

  img {
    transform: translateX(5px);
  }
}

.event-link:active {
  opacity: 0.8;
}

@media (max-width: 768px) {
  .under-construction {
    margin-top: 169px;
  }

  .under-construction__header {
    row-gap: 20px;

    .under-construction__title {
      font-size: 36px;
    }

    .under-construction__subtitle {
      width: 286px;
      font-size: 16px;
    }
  }

  .event-block {
    margin-top: 40px;

    .event-block__title {
      width: 300px;
      font-size: 16px;
    }

    .event-link__wrapper {
      margin-top: 15px;
    }
  }
}

@media (max-width: 360px) {
  .under-construction {
    margin-top: 66px;
  }

  .under-construction__header {
    row-gap: 16px;

    .under-construction__title {
      font-size: 36px;
    }

    .under-construction__subtitle {
      width: 286px;
      font-size: 16px;
    }
  }

  .event-block {
    margin-top: 40px;

    .event-block__title {
      font-size: 16px;
    }
  }
}
</style>
