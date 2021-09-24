<template>
<div>
    <div class="time">{{ time }}</div>
    <button class="control_button" @click="startTimer()" v-bind:disabled=running>Start</button>
    <button class="control_button" @click="stopTimer()" v-bind:disabled=!running>Stop</button>
    <button class="control_button" @click="resetTimer()" v-bind:disabled=running>Reset</button>
</div>
</template>

<script>
export default {
    name: 'StopWatch',
    data(){
        return {
            time: '00:00:00.000',
            running: false,
            timeBegan: null,
            timeStopped: null,
            stoppedDuration: 0,
            started: null,
        }
    },
    methods:{
        startTimer() {
            if(this.running) return;

            if (this.timeBegan === null) {
              this.resetTimer();
              this.timeBegan = new Date();
            }

            if (this.timeStopped !== null) {
              this.stoppedDuration += (new Date() - this.timeStopped);
            }

            this.started = setInterval(this.timerRunning, 10);
            this.running = true
        },
        stopTimer() {
            this.running = false;
            this.timeStopped = new Date();
            clearInterval(this.started);
        },
        resetTimer() {
            this.running = false;
            clearInterval(this.started)
            this.stoppedDuration = 0;
            this.timeBegan = null;
            this.timeStopped = null;
            this.time = '00:00:00.000';
        },
        timerRunning(){
          const currentTime = new Date();
          const diff = currentTime - this.timeBegan - this.stoppedDuration;
          let timeElapsed = new Date(diff),
          hour = timeElapsed.getUTCHours(),
          min = timeElapsed.getUTCMinutes(),
          sec = timeElapsed.getUTCSeconds(),
          ms = timeElapsed.getUTCMilliseconds();

          const dateDiff = Math.floor(diff / (1000*60*60*24));
          if (dateDiff >= 1) {
            hour += dateDiff * 24;
          }

          this.time =
          this.zeroPrefix(hour, 3) + ":" +
          this.zeroPrefix(min, 2) + ":" +
          this.zeroPrefix(sec, 2) + "." +
          this.zeroPrefix(ms, 3);
        },
        zeroPrefix(num, digit) {
          let zero = ''
          for(let i = 0; i < digit; i++) {
            zero += '0';
          }
          return (zero + num).slice(-digit);
        }
    }
};
</script>

<style>
.time {
  font-size: 2.5rem;
  color: #00bfff;
  text-align: center;
}
.control_button {
  margin: 2px;
  width: 4rem;
  height: 2rem;
}
</style>