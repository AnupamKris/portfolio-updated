<template>
  <div class="sidenav">
    <div class="link" @click="changeTab(0)">
      <p>home</p>
    </div>
    <div class="link" @click="changeTab(1)">
      <p>info</p>
    </div>
    <div class="link" @click="changeTab(2)">
      <p>achievements</p>
    </div>
    <div class="link" @click="changeTab(3)">
      <p>projects</p>
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(["changeTab"]);

const changeTab = (index) => {
  emit("changeTab", index);
  console.log("Chagning to ", index);
};
</script>

<style lang="scss" scoped>
.sidenav {
  width: 120px;
  z-index: 15;

  // background: #4d4d4d;
  right: 0;
  top: 0;
  position: fixed;
  z-index: 2;
  display: flex;
  flex-direction: column;
  padding-top: 50px;
  // justify-content: space-around;
  // align-items: center;
  //   backdrop-filter: blur(10px);

  .link {
    display: flex;
    justify-content: center;
    align-items: center;

    width: 100%;
    height: 100%;
    cursor: pointer;

    &:hover p {
      color: #57b9fa;
    }
  }

  .link::after {
    content: "";
    position: absolute;
    inset: 0;
    z-index: -1;

    height: 100%;
    width: 100%;

    // background: red;
    // mask: linear-gradient(to top, transparent, black 50%);
    mask: radial-gradient(closest-side, black 0%, transparent 100%);
    // backdrop-filter: blur(10px);
  }

  p {
    text-decoration: none;
    color: white;
    transform: rotate(-90deg);

    transition: 0.3s;

    display: flex;
    justify-content: center;
    align-items: center;
    font-family: Consolas, monaco, monospace;
    font-size: 18px;

    width: 100%;
  }

  :nth-child(1) {
    height: 70px;
  }
  :nth-child(2) {
    height: 90px;
  }
  :nth-child(3) {
    height: 180px;
  }
  :nth-child(4) {
    height: 130px;
  }
}

@media (max-width: 600px) {
  .sidenav {
    display: none;
  }
}
</style>
