<template>
  <div>
    <div class='wrapper'>
      <!-- Clockコンポーネントを表示 -->
      <Clock class="clock mx-auto my-5" />
    </div>
  </div>
</template>

<script>
import Clock from "./components/WorldClock"

export default {
  components: {
    Clock,
  },
}
</script>

<style scoped>
.clock {
  width: 80%;
  max-width: 600px;
}
</style>

<style>
@font-face {
  font-family: 'D7MBI';
  src: url('digital-7_mono.ttf');
}

html {
  font-size: 80%;
}

body {
  background: #000;
}

.wrapper{
  /* margin: 50px auto; */
  margin: 0 auto;
  width: 960px;
}

p {
  margin: 0;
}
</style>