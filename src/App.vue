<template>
  <div id="app">
    <div v-for="(value, index) in Array(100)" :key="index" :class="`animation${index + 1}`"></div>
  </div>
</template>

<script>

export default {
  name: 'app'
}
</script>

<style lang="scss">
@use "sass:math";

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 100%;
  height: 100%;
  position: relative;
}

@for $i from 1 through 100 {
  $size: math.ceil(math.random() * 300px + 30px);
  $color: rgb(math.random() * 255, math.random() * 255, math.random() * 255);

  .animation#{$i} {
    box-sizing: border-box;
    position: absolute;
    left: math.random() * 900px;
    top: math.random() * 600px;
    border-radius: 50%;

    border-width: 0;
    border-style: solid;
    border-color: $color;
    background-color: $color;
    width: $size;
    height: $size;
    opacity: 0;
    z-index: math.ceil(math.random() * 100);
    animation: scale-#{$i} math.random() * 2 + 3s math.random() * 30 + 1s infinite normal;
  }

  @keyframes scale-#{$i} {
    0% {
      transform: scale(0);
      opacity: 1;
      background-color: $color;
      border-width: 0;
    }
    20%{
      opacity: 1;
      background-color: $color;
      border-width: $size / 2;
    }

    40% {
      opacity: .8;
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
