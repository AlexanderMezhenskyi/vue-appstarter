<template>
  <div class="timer-item">
    <span class="name">{{timer.name}}</span>
    <span class="time" :class="{'no-running': !timer.isRunning}">
        {{timer.time}}
    </span>
    <button class="btn-pause" v-if="timer.isRunning" @click="timerPause">
      <i class="mdi mdi-pause"></i>
    </button>
    <button class="btn-play" v-else @click="timerRun">
      <i class="mdi mdi-play"></i>
    </button>
    <button class="btn-delete" @click="timerDelete">
      <i class="mdi mdi-delete"></i>
    </button>
  </div>
</template>

<script>
export default {
  name: 'TimerItem',
  props: {
    timer: {
      type: Object,
      required: true,
    },
  },
  methods: {
    timerRun() {
      this.timer.isRunning = true;

      if (this.timer.pauseStartTime) {
        this.timer.pauseTime += new Date().getTime() - this.timer.pauseStartTime;
      }

      if (!this.timer.timerInterval) {
        this.timer.timerInterval = setInterval(() => {
          this.timer.time = this.calcTime(this.timer);
        }, 1000);
      }

      return this.timer.time;
    },
    timerPause() {
      clearInterval(this.timer.timerInterval);
      this.timer.timerInterval = '';
      this.timer.pauseStartTime = new Date().getTime();
      this.timer.isRunning = false;
    },
    timerDelete() {
      clearInterval(this.timer.timerInterval);
      this.$emit('onTimerDelete', this.timer);
    },
    calcTime() {
      const time = new Date() - this.timer.startTime - (this.timer.pauseTime ?? 0);
      this.timer.hours = Math.floor((time % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      this.timer.minutes = Math.floor((time % (1000 * 60 * 60)) / (1000 * 60));
      this.timer.seconds = Math.floor((time % (1000 * 60)) / 1000);

      return `${this.timer.hours}:${this.timer.minutes}:${this.timer.seconds}`;
    },
  },
  mounted() {
    if (this.timer.isRunning) {
      this.timerPause();
      this.timerRun();
    } else {
      this.timerPause();
    }
  },
};
</script>

<style scoped lang="scss">
  .timer-item {
    max-width: 490px;
    display: flex;
    align-items: center;
    padding-bottom: 39px;
    margin: 0 auto;
    @media screen and (max-width: 767px) {
      justify-content: space-between;
    }
    @media screen and (max-width: 399px) {
      flex-wrap: wrap;
      padding: 10px 0 15px;
      border-bottom: 1px solid #E7E8EA;
    }
    &:last-of-type {
      padding-bottom: 0;
      @media screen and (max-width: 399px) {
        padding: 10px 0 0;
        border-bottom: none;
      }
    }
    .name {
      width: 170px;
      font-weight: 800;
      font-size: 20px;
      line-height: 30px;
      color: #5586F2;
      margin-right: 16px;
      white-space: nowrap;
      text-overflow: ellipsis;
      overflow: hidden;
      @media screen and (max-width: 767px) {
        width: 150px;
        font-size: 18px;
        margin: 0;
      }
      @media screen and (max-width: 399px) {
        width: 100%;
      }
    }
    .time {
      width: 119px;
      height: 51px;
      font-size: 17px;
      line-height: 23px;
      color: #676C75;
      background: #E7E8EA;
      border: 1px solid #E7E8EA;
      border-radius: 6px;
      padding: 13px 0;
      margin-right: 41px;
      text-align: center;
      white-space: nowrap;
      @media screen and (max-width: 767px) {
        width: 90px;
        height: 30px;
        padding: 3px 0;
        margin: 0;
      }
      &.no-running {
        background: rgba(255, 72, 118, 0.15);
        border: 1px solid rgba(255, 72, 118, 0.15);
      }
    }
    button {
      width: 50px;
      height: 50px;
      color: #fff;
      box-shadow: 0 6px 12px rgba(40, 43, 49, 0.08);
      margin-right: 20px;
      @media screen and (max-width: 767px) {
        width: 30px;
        height: 30px;
        margin: 0;
      }
      i {
        font-size: 150%;
        @media screen and (max-width: 767px) {
          font-size: 100%;
        }
      }
    }
    .btn-play,
    .btn-pause {
      border-radius: 50%;
    }
    .btn-play {
      background: linear-gradient(135deg, #009FC5 0%, #3CECB0 100%);
    }
    .btn-pause {
      background: linear-gradient(135deg, #7956EC 0%, #2FB9F8 100%);
    }
    .btn-delete {
      background: linear-gradient(135deg, #F23673 0%, #FCA069 100%);
      border-radius: 6px;
    }
  }
</style>
