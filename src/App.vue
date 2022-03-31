<template>
  <div>
    <div class='wrapper'>
      <div class="nav">
        <button class="btn btn-outline-light" @click="handleOpenJapanClock">日本</button>
        <button class="btn btn-outline-light" @click="handleOpenAustraliaClock">豪州</button>
        <button class="btn btn-outline-light" @click="handleOpenChinaClock">中国</button>
        <button class="btn btn-outline-light" @click="handleOpenUKClock">英国</button>
        <button class="btn btn-outline-light" @click="handleOpenUSClock">米国</button>
      </div>
        <div class='clocks'>
          <Clock
            class="clock mx-auto my-5"
            location="日本" :diff="0"
            v-if="showJapanClock"
            @close-clock="handleCloseJapanClock"
          />
          <Clock
            class="clock mx-auto my-5"
            location="豪州" :diff="+2"
            v-if="showAustraliaClock"
            @close-clock="handleCloseAustraliaClock"
            />
          <Clock
            class="clock mx-auto my-5"
            location="中国" :diff="-1"
            v-if="showChinaClock"
            @close-clock="handleCloseChinaClock"
            />
          <Clock
            class="clock mx-auto my-5"
            location="英国" :diff="-9"
            v-if="showUKClock"
            @close-clock="handleCloseUKClock"
            />
          <Clock
            class="clock mx-auto my-5"
            location="米国" :diff="-14"
            v-if="showUSClock"
            @close-clock="handleCloseUSClock"
            />
        </div>
    </div>
  </div>
</template>

<script>
import Clock from "./components/WorldClock"

export default {
  data() {
    return {
      // デフォルト：falseでは表示しない設定にする
      showJapanClock: false,
      showAustraliaClock: false,
      showChinaClock: false,
      showUKClock: false,
      showUSClock: false,
    }
  },
  components: {
    Clock,
  },
  methods: {
    handleOpenJapanClock() {
      this.showJapanClock = true;
    },
    handleCloseJapanClock() {
      this.showJapanClock = false;
    },
    handleOpenAustraliaClock() {
      this.showAustraliaClock = true;
    },
    handleCloseAustraliaClock() {
      this.showAustraliaClock = false;
    },
    handleOpenChinaClock() {
      this.showChinaClock = true;
    },
    handleCloseChinaClock() {
      this.showChinaClock = false;
    },
    handleOpenUKClock() {
      this.showUKClock = true;
    },
    handleCloseUKClock() {
      this.showUKClock = false;
    },
    handleOpenUSClock() {
      this.showUSClock = true;
    },
    handleCloseUSClock() {
      this.showUSClock = false;
    }
  }
}
</script>

<style scoped>
.clock {
  width: 80%;
  max-width: 600px;
}

.nav{
  margin-top: 20px;
}

button{
  margin: 0px 10px;
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