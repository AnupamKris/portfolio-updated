<template>
  <div class="typer">
    <div class="text">
      <span v-for="(char, index) in currentText" :key="index">
        <span>{{ char }}</span>
      </span>
      <span class="cursor" v-if="cursor">|</span>
      <span v-else>&nbsp;</span>
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
    default: 100,
  },
  cursor: {
    type: Boolean,
    default: true,
  },
});

const currentText = ref("");
const currentTextIndex = ref(0);
const currentIndex = ref(0);
const mainInterval = ref(null);
const subInterval = ref(null);

onMounted(() => {
  mainInterval.value = setInterval(() => {
    if (currentTextIndex.value === props.text.length - 1) {
      currentTextIndex.value = 0;
    } else {
      currentTextIndex.value++;
    }
    currentIndex.value = 0;
    subInterval.value = setInterval(() => {
      if (currentIndex.value > props.text[currentTextIndex.value].length) {
        clearInterval(subInterval.value);
        return;
      }
      currentText.value = props.text[currentTextIndex.value].slice(
        0,
        currentIndex.value
      );
      currentIndex.value++;
      //   console.log(currentText.value);
    }, props.delay);
    // reverse

    setTimeout(() => {
      subInterval.value = setInterval(() => {
        if (currentIndex.value < 0) {
          clearInterval(subInterval.value);
          return;
        }
        currentText.value = props.text[currentTextIndex.value].slice(
          0,
          currentIndex.value
        );
        currentIndex.value--;
        // console.log(currentText.value);
      }, props.delay);
    }, props.delay * props.text[currentTextIndex.value].length + 1000);
  }, props.delay * props.text[currentTextIndex.value].length * 2 + 2000);
});

onBeforeUnmount(() => {
  clearInterval(mainInterval.value);
  clearInterval(subInterval.value);
});
</script>

<style lang="scss" scoped>
.cursor {
  animation: blink 0.75s infinite;
  color: #666666;
  font-weight: 400;
}

@keyframes blink {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
</style>
