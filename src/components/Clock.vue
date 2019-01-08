<template>
  <div class="clock">
    <img src="/assets/clock.svg" alt="Clock"/>
    <div class="counter">{{ counter }}</div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      counter: null
    }
  },
  methods: {
    async countdown (second) {
      return new Promise(resolve => {
        this.counter = second;
        const interval = setInterval(() => {
          this.counter -= 1;
          if (this.counter == 0) {
            clearInterval(interval);
            resolve();
          }
        }, 1000);
      });
    }
  }
}
</script>

<style>
.clock {
  width: 50px;
  height: 50px;
  position: absolute;
  left: 150px;
  top: 212.5px;
  text-align: center;
}

.clock img {
  width: 100%;
  height: 100%;
}

.clock .counter {
  position: absolute;
  top: 0px;
  left: 0px;
  bottom: 0px;
  right: 0px;
  margin: auto;
  width: 40px;
  height: 40px;
  text-align: center;
  line-height: 45px;
  font-weight: bold;
}
</style>