<template>
  <div>
    <div class="container">
      <!-- デジタル時計の枠 -->
      <div class="time-cover">
        <p class="time-item">00:00:00</p>
      </div>
      <div class="clock-field">
        <!-- 日付・計測値（国） -->
        <div class="sub-menus">
          <p class="date">{{ year }}.{{ month }}.{{ day }}</p>
          <p class="location">{{ location }}</p>
        </div>
        <div class="time">
          <button type="button" class="btn btn-outline-light" @click="handleCloseClock">CLOSE</button>
          <!-- デジタル時計 -->
          <p class="time-item pt-2">{{ hours }}:{{ minutes }}:{{ seconds }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// 時間が一桁の時のみ、10のくらいに「0」を表示する処理
const zeroPadding = (num, digit) => {
  return (Array(digit).join("0") + num).slice(-digit)
}

export default {
  props: ["location", "diff"],
  data() {
    return {
      // 本日の日付を定義
      date: new Date(),
    }
  },
  // 算出プロパティでdateから「年」、「月」、「日」、「時間」、「分」、「秒」をそれぞれ取得するメソッドを定義しておく
  computed: {
    // 年を取得
    year() {
      return this.date.getFullYear()
    },
    // 月を取得
    month() {
      return zeroPadding(this.date.getMonth() + 1, 2)
    },
    // 日を取得
    day() {
      return zeroPadding(this.date.getDate(), 2)
    },
    // 時間を取得
    hours() {
      return zeroPadding(this.date.getHours(), 2)
    },
    // 分を取得
    minutes() {
      return zeroPadding(this.date.getMinutes(), 2)
    },
    // 秒を取得
    seconds() {
      return zeroPadding(this.date.getSeconds(), 2)
    },
  },
  mounted() {
    this.setDate()
    // 1秒ごとに、更新された日付を取得しsetDateメソッドを繰り返す
    setInterval(() => this.setDate(), 1000)
  },
  methods: {
    // 更新された日付をdateに格納するメソッド
    setDate() {
      this.date = new Date()
      this.date.setHours(this.date.getHours() + this.diff)
    },
    handleCloseClock() {
      this.$emit('close-clock')
    },
  },
}
</script>

<style scoped>
.container {
  border: 2px solid;
  border-color: #fff;
  padding: 10px 10px 0px 10px;
}

.date {
  font-family: 'D7MBI';
  font-size: 2.5rem;
  letter-spacing: .1em;
  margin-bottom:  10px;
  line-height: 1;
}

.clock-field{
  display: flex;
  justify-content: space-between;
}

.sub-menus{
  margin: 0px 10px 10px 0px;
  text-align: center;
  color: #fff;
}

.location{
  font-size: 80px;
  font-family: serif;
  line-height: 1;
}

.time-cover {
  position: absolute;
  align-items: center;
  margin-top: 37.5px;
  margin-left: 204px;
  z-index: 0;
}

.time {
  color: #fff;
  z-index: 50;
  /* padding-top: 1.1%; */
}

.time-item {
  height: 100px;
  font-family: 'D7MBI';
  font-size: 8rem;
  line-height: 1;
  box-sizing: border-box;
}

.btn{
  margin-left: 305px;
}
</style>