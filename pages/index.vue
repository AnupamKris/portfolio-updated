<template>
  <div class="fixed-parrallax">
    <DecorativeSquare :x="20" :y="33" :width="30" :thickness="30" />
    <DecorativeSquare :x="5" :y="66" :width="40" :thickness="30" />
    <DecorativeSquare :x="70" :y="15" :width="60" :thickness="50" />
    <DecorativeSquare :x="90" :y="90" :width="120" :thickness="90" />
  </div>
  <SideNav @changeTab="changeTab" />
  <Home
    :subTextPosition="subTextPosition"
    :mainTextPosition="mainTextPosition"
  />
  <div class="info">
    <h1>About Me</h1>
    <!-- <div class="profile">
      <img src="@/assets/prof.png" alt="" />
    </div> -->
    <div class="container">
      <div class="bio">
        Hi, I am Anupam Krishna, Welcome to my digital space! I'm an aspiring AI
        and Data Science specialist currently pursuing my Bachelor's at
        Prathyusha Engineering College. A tech enthusiast at heart, I constantly
        explore the latest software releases. My passion for programming has
        driven me to create diverse projects, spanning Frontend, Backend,
        Desktop Apps, LLM, and Data Science. Rooted in a solid engineering
        foundation, I'm on a mission to leverage AI and Data Science for
        real-world problem-solving. My journey reflects a commitment to
        continuous learning, evident in each project that showcases the fusion
        of innovation and skill. Join me on this tech odyssey, where my goal is
        to contribute to a future shaped by the transformative power of
        technology.
      </div>
      <div class="skillset">
        <h3>Skillset</h3>
        <div class="skills">
          <h3>Programming Languages</h3>
          <div class="items">
            <p>Python</p>
            <p>JavaScript</p>
            <p>SQL</p>
          </div>
        </div>
        <div class="skills">
          <h3>Designing</h3>
          <div class="items">
            <p>Figma</p>
            <p>Blender</p>
            <p>Canva</p>
          </div>
        </div>
        <div class="skills">
          <h3>Frontend</h3>
          <div class="items">
            <p>ReactJS</p>
            <p>VueJS</p>
            <p>Nuxt3</p>
            <p>SCSS</p>
          </div>
        </div>
        <div class="skills">
          <h3>Backend & Database</h3>
          <div class="items">
            <p>MongoDB</p>
            <p>Firebase</p>
            <p>SQL</p>
            <p>NodeJS</p>
            <p>SocketIO</p>
            <p>Flask</p>
            <p>Bottle</p>
          </div>
        </div>
        <div class="skills">
          <h3>AI & Data Science</h3>
          <div class="items">
            <p>OpenCV</p>
            <p>Torch</p>
            <p>GenAI</p>
            <p>llama.cpp</p>
            <p>MatplotLib</p>
            <p>Seaborn</p>
            <p>Pandas</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const tabs = ["home", "info", "achievements", "projects"];

const currentTab = ref(0);

const changeTab = (index) => {
  currentTab.value = index;
  let tab = document.querySelector(`.${tabs[index]}`);
  console.log("Chagning to ", index);
  tab.scrollIntoView({ behavior: "smooth" });
};

const scrollPosition = ref(0);
const subTextPosition = computed(() => {
  return scrollPosition.value / 2;
});
const mainTextPosition = computed(() => {
  return scrollPosition.value / 3;
});

const showSrollPos = () => {
  let el = document.querySelector("html");
  console.log(el.scrollTop);
};

onMounted(() => {
  let element = document.querySelector("html");
  // console.log(element, element.scrollTop);
  window.addEventListener("scroll", () => {
    scrollPosition.value = element.scrollTop;
  });

  scrollPosition.value = element.scrollTop;
});
</script>

<style lang="scss" scoped>
.info {
  height: 100vh;
  width: 100%;

  background: #141414;

  display: flex;

  flex-direction: column;
  // justify-content: center;
  // align-items: center;

  padding-top: 110px;
  padding-left: 50px;

  scroll-snap-align: center;

  .container {
    display: flex;
    // justify-content: center;
    // align-items: center;

    padding-right: 120px;
  }

  .bio {
    color: #ffffff;
    font-size: 24px;
    font-family: consolas;
    font-weight: 400;
    padding-right: 120px;
    margin-bottom: 20px;
    text-align: justify;
    width: 50%;
  }

  .skillset {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;

    width: 50%;

    h3 {
      width: 100%;
      color: #ffffff;
      font-size: 26px;
      font-family: consolas;
      font-weight: 600;

      margin-bottom: 10px;
    }
  }

  .skills {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    width: 100%;
    margin-top: 20px;

    h3 {
      width: 100%;
      color: #ffffff;
      font-size: 18px;
      font-family: consolas;
      font-weight: 400;

      margin-bottom: 10px;
    }

    .items {
      display: flex;
      justify-content: flex-start;
      align-items: center;

      width: 100%;
    }

    p {
      color: #141414;
      background: #ffffff;

      border-radius: 5px;
      padding: 5px 10px;
      font-size: 18px;
      font-family: consolas;
      font-weight: 400;

      margin-right: 10px;
    }
  }

  .profile {
    height: 500px;
    // width: 500px;
    // border-radius: 50%;

    position: relative;

    overflow: hidden;

    img {
      height: 100%;
      filter: drop-shadow(5px 5px 1px #ececec);
    }

    /* you need to match the shadow color to your background or image border for the desired effect*/
    box-shadow: 0 0 50px 50px #141414 inset;
  }
  h1 {
    color: #ffffff;
    font-size: 128px;
    font-family: consolas;

    z-index: 5;

    // background: linear-gradient(to right, #2747ff, #27ffac);
    // -webkit-background-clip: text;
    // -webkit-text-fill-color: transparent;
  }
}

.fixed-parrallax {
  position: fixed;
  height: 100vh;
  width: 100%;
  z-index: 2;

  animation: parallax-side linear;
  animation-timeline: scroll();
  pointer-events: none;
}

@keyframes parallax-side {
  0% {
    transform: translate(0px, 0px);
  }
  100% {
    transform: translate(0px, -50vh);
  }
}

@keyframes parallax-1 {
  0% {
    transform: translate(0px, 0px);
  }
  100% {
    transform: translate(0px, -50vh);
  }
}
</style>
