<script setup>
import { ref, computed, onMounted, onUnmounted, defineProps } from "vue"

const props = defineProps({
  endDateObject: {
    day: Number,
    month: Number,
    year: Number,
  },
})

const targetDate = ref(
  new Date(
    props.endDateObject.year,
    props.endDateObject.month - 1,
    props.endDateObject.day
  )
)
const now = ref(new Date())

const updateNow = () => {
  now.value = new Date()
}

const timeLeft = computed(() => {
  const diff = targetDate.value - now.value
  if (diff <= 0) {
    return { days: "00", hours: "00", minutes: "00", seconds: "00" }
  }
  const days = String(Math.floor(diff / (1000 * 60 * 60 * 24))).padStart(2, "0")
  const hours = String(Math.floor((diff / (1000 * 60 * 60)) % 24)).padStart(
    2,
    "0"
  )
  const minutes = String(Math.floor((diff / (1000 * 60)) % 60)).padStart(2, "0")
  const seconds = String(Math.floor((diff / 1000) % 60)).padStart(2, "0")
  return { days, hours, minutes, seconds }
})

let intervalId
onMounted(() => {
  intervalId = setInterval(updateNow, 1000)
})

onUnmounted(() => {
  clearInterval(intervalId)
})
</script>

<template>
  <div class="countdown-timer">
    <div class="countdown-timer__numbers-row">
      <div class="countdown-timer__number number">{{ timeLeft.days }}</div>
      <span class="separator">:</span>
      <div class="countdown-timer__number number">{{ timeLeft.hours }}</div>
      <span class="separator">:</span>
      <div class="countdown-timer__number number">{{ timeLeft.minutes }}</div>
      <span class="separator">:</span>
      <div class="countdown-timer__number number">{{ timeLeft.seconds }}</div>
    </div>
    <div class="countdown-timer__flyers-row">
      <div class="number__flyer">Days</div>
      <div class="number__flyer">Hours</div>
      <div class="number__flyer">Minutes</div>
      <div class="number__flyer">Seconds</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.countdown-timer {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 4px;
  margin-top: 32px;
}

.countdown-timer__numbers-row {
  display: flex;
}

.countdown-timer__flyers-row {
  display: flex;
  column-gap: 20px;
}

.number {
  width: 132px;
  text-align: center;
  align-items: center;
  font-weight: 600;
  font-size: 72px;
  line-height: 100%;
  color: #162c4e;
}

.number__flyer {
  position: relative;
  text-align: center;
  width: 132px;
  height: 55px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 400;
  font-size: 16px;
  line-height: 100%;
  background-color: #df2224;
  color: #ffffff;
  clip-path: polygon(
    0% 100%,
    0% 100%,
    1.546% 94.208%,
    3.167% 89.47%,
    4.89% 85.682%,
    6.741% 82.739%,
    8.747% 80.536%,
    10.936% 78.968%,
    13.332% 77.931%,
    15.964% 77.32%,
    18.858% 77.03%,
    22.041% 76.957%,
    22.041% 76.957%,
    25.439% 76.938%,
    28.971% 76.891%,
    32.657% 76.827%,
    36.514% 76.76%,
    40.562% 76.7%,
    44.818% 76.661%,
    49.301% 76.655%,
    54.029% 76.694%,
    59.022% 76.79%,
    64.297% 76.957%,
    64.297% 76.957%,
    69.991% 76.42%,
    75.364% 74.349%,
    80.357% 70.723%,
    84.916% 65.52%,
    88.985% 58.719%,
    92.506% 50.299%,
    95.425% 40.238%,
    97.684% 28.515%,
    99.228% 15.11%,
    100% 0%,
    100% 0%,
    98.434% 5.848%,
    96.758% 10.736%,
    94.956% 14.747%,
    93.008% 17.961%,
    90.896% 20.458%,
    88.602% 22.32%,
    86.109% 23.627%,
    83.397% 24.461%,
    80.448% 24.902%,
    77.245% 25.031%,
    77.245% 25.031%,
    74.026% 25.049%,
    70.978% 25.097%,
    68.007% 25.16%,
    65.016% 25.228%,
    61.912% 25.287%,
    58.6% 25.326%,
    54.983% 25.332%,
    50.969% 25.293%,
    46.46% 25.197%,
    41.364% 25.031%,
    41.364% 25.031%,
    35.66% 25.549%,
    30.237% 27.563%,
    25.121% 31.093%,
    20.337% 36.162%,
    15.91% 42.787%,
    11.864% 50.991%,
    8.226% 60.794%,
    5.019% 72.216%,
    2.268% 85.278%,
    0% 100%
  );
}

.separator {
  font-weight: 600;
  font-size: 72px;
  line-height: 100%;
  color: #162c4e;
}

@media (max-width: 768px) {
  .countdown-timer {
    row-gap: 6px;
    margin-top: 40px;

    .countdown-timer__numbers-row {
      column-gap: 12px;

      .number {
        width: 64px;
        font-size: 36px;
      }

      .separator {
        font-size: 36px;
      }
    }

    .countdown-timer__flyers-row {
      column-gap: 34px;

      .number__flyer {
        width: 64px;
        height: 40px;
        font-size: 12px;
      }
    }
  }
}

@media (max-width: 360px) {
  .countdown-timer {
    .countdown-timer__numbers-row {
      column-gap: 4px;
    }

    .countdown-timer__flyers-row {
      column-gap: 18px;
    }
  }
}
</style>
