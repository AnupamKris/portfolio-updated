<template>
  <div class="home">
    <div class="logo" @click="showSrollPos">AnupamKris</div>

    <div class="text">
      <div
        class="bgtext"
        :style="{ transform: `translate(0, -${mainTextPosition}px)` }"
      >
        <Flipper :cursor="false" :text="aitexts" :delay="2000" />
        <Flipper
          :cursor="false"
          :text="webtexts"
          class="small"
          :colors="webcolors"
          :delay="2700"
        />
      </div>
      <div class="mtext">
        <span>
          Hello
          <p>.</p></span
        >
        <span>I am </span>
        <span>Anupam</span>
      </div>
      <div
        class="subtext"
        :style="{
          transform: `rotateZ(-90deg) translate(${subTextPosition}px, 0)`,
        }"
      >
        <p>Artificial Intelligence</p>
        <p>& Web Development</p>
        <p>Enthusiast</p>
      </div>
    </div>
  </div>
</template>

<script setup>
let aitexts = ["Gen AI", "ML", "LLMs", "DL", "NLP"];
let webtexts = ["JavaScript", "Vue", "React", "Node", "Flask", "MongoDB"];
let webcolors = [
  "#f7df1e22",
  "#48ff7f22",
  "#61dafb22",
  "#94c84822",
  "#222222",
  "#08ee6922",
];

const props = defineProps({
  mainTextPosition: Number,
  subTextPosition: Number,
});
</script>

<style lang="scss" scoped>
.home {
  height: 100vh;
  width: 100%;

  background: #141414;

  display: flex;
  justify-content: flex-end;
  align-items: center;

  scroll-snap-align: center;

  .logo {
    height: 50px;
    width: auto;
    top: 50px;
    left: 50px;
    font-family: "Amsterdam four_ttf";
    position: fixed;
    color: white;
  }

  .text {
    height: 100%;
    max-height: 100%;
    width: 100%;
    color: #ffffff;

    font-size: 200px;
    line-height: 250px;
    font-weight: 600;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-end;

    position: relative;
    pointer-events: none;
    overflow-y: visible;
    // overflow: visible;

    .bgtext {
      position: absolute;
      color: #222222;
      font-size: 512px;
      line-height: 600px;
      left: 100px;
      top: 0;

      display: flex;
      flex-direction: column;

      height: 100%;
      width: 100%;

      opacity: 0.7;

      // .small {
      //   font-size: 256px;
      //   line-height: 300px;
      // }
    }
    .mtext {
      width: 1000px;
      z-index: 5;
      span {
        display: flex;
        //   justify-content: center;
        align-items: center;
        z-index: 2;

        p {
          color: #ff5588;
        }
      }
    }

    .subtext {
      font-size: 16px;
      line-height: 40px;
      font-weight: 400;
      z-index: 6;
      // margin-top: 20px;

      position: absolute;
      left: 30px;
      bottom: 100px;

      display: flex;
      flex-direction: column;
      transform: rotateZ(-90deg);

      animation: parallax-1 linear;
      animation-timeline: scroll();

      p {
        font-family: consolas;
        font-weight: 600;
      }
    }
  }
}

@media screen and (max-width: 768px) {
  .home {
    .text {
      justify-content: flex-start;
      .bgtext {
        font-size: 128px;
        line-height: 300px;
        flex-direction: column;
        width: 100%;
        height: 400px;
        padding: 0;
        margin: 0;
        bottom: 50px;
        top: auto;
        .flipper {
          height: 200px;
          z-index: 10;
          overflow-y: visible;
        }
      }
      .mtext {
        height: auto;
        width: 100%;
        padding: 0 20px;
        padding-top: 170px;

        // display: flex;
        // flex-direction: column;
        span {
          font-size: 72px;
          line-height: 96px;
        }
      }
      .subtext {
        font-size: 12px;
        line-height: 20px;
        left: 15px;
        // bottom: 50px;
      }
    }
  }
}
</style>
