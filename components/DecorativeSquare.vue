<template>
  <div
    class="decor"
    :style="{
      top: y + '%',
      left: x + '%',
      width: width + 'px',
      height: width + 'px',
      border: thickness + 'px solid #92929277',
    }"
  >
    <!-- <div
      class="inblack"
      :style="{
        width: `calc(100% - ${thickness}px)`,
        height: `calc(100% - ${thickness}px)`,
      }"
    ></div> -->
  </div>
</template>

<script setup>
const props = defineProps({
  x: {
    type: Number,
    default: 0,
  },
  y: {
    type: Number,
    default: 0,
  },
  width: {
    type: Number,
    default: 100,
  },
  thickness: {
    type: Number,
    default: 40,
  },
});
</script>

<style lang="scss" scoped>
.decor {
  border: 60px solid #92929277;
  background: inherit;
  border-radius: 40%;
  position: absolute;

  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1;
  box-sizing: content-box;
}
</style>
