<template>
  <div class="flipper">
    <div
      class="card"
      :class="currentIndex == index ? 'active' : ''"
      :style="{ color: colors.length > 0 ? props.colors[index] : 'inherit' }"
      v-for="(item, index) in text"
    >
      {{ item }}
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  text: {
    type: Array,
    required: true,
  },
  delay: {
    type: Number,
    default: 1000,
  },
  colors: {
    type: Array,
    default: () => [],
  },
});

const currentIndex = ref(0);
const interval = ref(null);

onMounted(() => {
  interval.value = setInterval(() => {
    if (currentIndex.value === props.text.length - 1) {
      currentIndex.value = 0;
    } else {
      currentIndex.value++;
    }
    // console.log(currentIndex.value);
  }, props.delay);
});

onUnmounted(() => {
  clearInterval(interval.value);
});
</script>

<style lang="scss" scoped>
.flipper {
  height: 100%;
  width: 100%;
  overflow: hidden;
}
.card {
  backface-visibility: hidden;
  transform: rotateX(90deg);
  transition: 0.3s;
  height: 0;
}
.active {
  transform: rotateX(0deg);
}
</style>
