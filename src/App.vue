<template>
  <div id="app">
    <header>
      <ul>
        <li>
          <a href="https://github.com/rhythm191/dart-sass-bubble"
            ><img src="/github.svg" class="sns-icon" /><span class="sr-only"
              >Github</span
            ></a
          >
        </li>
        <li>
          <a
            href="https://twitter.com/intent/tweet?text=dart-sass-bubble&url=https://dart-sass-bubble.rhyztech.net/"
            ><img src="/twitter.svg" class="sns-icon" /><span class="sr-only"
              >Twitter</span
            ></a
          >
        </li>
        <li>
          <a
            href="https://www.facebook.com/sharer.php?u=https://dart-sass-bubble.rhyztech.net/&t=dart-sass-bubble"
            ><img src="/facebook.svg" class="sns-icon" /><span class="sr-only"
              >facebook</span
            ></a
          >
        </li>
      </ul>
    </header>
    <div class="canvas">
      <div
        v-for="(value, index) in Array(100)"
        :key="index"
        :class="`animation${index + 1}`"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app"
};
</script>

<style lang="scss">
@use "sass:math";

#app {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  flex: 0 1 auto;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100vw;
  max-width: 900px;
  height: 100vh;
  margin: 0 auto;
  @media screen and (max-width: 899px) {
    overflow: hidden;
  }
}

header {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 40px;

  ul {
    margin: 0;
    padding: 0;
    list-style: none;

    li {
      display: inline-block;
      margin-right: 24px;
    }
  }
}

.sns-icon {
  width: 32px;
  height: 32px;
}

.sr-only {
  position: absolute !important;
  width: 1px !important;
  height: 1px !important;
  padding: 0 !important;
  margin: -1px !important;
  overflow: hidden !important;
  clip: rect(0, 0, 0, 0) !important;
  white-space: nowrap !important;
  border: 0 !important;
}

.canvas {
  position: relative;
  width: 100%;
  height: 100%;
}

@for $i from 1 through 100 {
  $size: math.ceil(math.random() * 300px + 30px);
  $color: rgb(math.random() * 255, math.random() * 255, math.random() * 255);

  .animation#{$i} {
    box-sizing: border-box;
    position: absolute;
    left: math.random() * 100%;
    top: math.random() * 100%;
    border-radius: 50%;

    border-width: 0;
    border-style: solid;
    border-color: $color;
    background-color: $color;
    width: $size;
    height: $size;
    opacity: 0;
    z-index: math.ceil(math.random() * 100);
    animation: scale-#{$i}
      math.random() * 2 + 3s
      math.random() * 30 + 1s
      infinite
      normal;
  }

  @keyframes scale-#{$i} {
    0% {
      transform: scale(0);
      opacity: 1;
      background-color: $color;
      border-width: 0;
    }
    20% {
      opacity: 1;
      background-color: $color;
      border-width: $size / 2;
    }

    40% {
      opacity: 0.8;
      background-color: transparent;
    }

    70% {
      transform: scale(1);
    }
    100% {
      opacity: 0;
      transform: scale(1);
    }
  }
}
</style>
