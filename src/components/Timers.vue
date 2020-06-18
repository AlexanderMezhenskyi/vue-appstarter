<template>
  <div class="timers-container">
    <div class="create-timer-container">
      <div class="create-timer-wrap">
        <input type="text" placeholder="Timer Name"
               v-model.trim="newTimer" @keypress.enter="addTimer">
        <button type="button" class="create-timer" @click="addTimer">Create Timer</button>
      </div>
    </div>
    <div class="timers-list">
      <template v-if="timers.length" >
        <TimerItem v-for="timer in timers" :key="'timer-' + timer.id" :timer="timer"
                   @onTimerDelete="deleteTimer"/>
      </template>
      <template v-else>
        <div class="list-empty">The timer list is empty. You could add a first timer.</div>
      </template>
    </div>
  </div>
</template>

<script>
import TimerItem from './TimerItem.vue';

const timersStorage = {
  uid: 0,
  getTimers() {
    const timers = JSON.parse(localStorage.getItem('appStarterTimers') || '[]');

    timers.forEach((timer, index) => {
      // eslint-disable-next-line no-param-reassign
      timer.id = index;
    });

    this.uid = timers.length;

    return timers;
  },
  saveTimers(timers) {
    localStorage.setItem('appStarterTimers', JSON.stringify(timers));
  },
};

export default {
  name: 'Timers',
  components: {
    TimerItem,
  },
  data() {
    return {
      timers: timersStorage.getTimers(),
      newTimer: '',
    };
  },
  methods: {
    addTimer(event) {
      let value = this.newTimer;

      if (!value && event.type !== 'click') {
        return;
      }

      if (!value && event.type === 'click') {
        const date = new Date();

        value = `Timer ${date.getDate()}/${date.getMonth()}/${date.getFullYear()}`;
      }

      this.timers.unshift({
        // eslint-disable-next-line no-plusplus
        id: timersStorage.uid++,
        name: value,
        time: '0:0:0',
        isRunning: true,
        startTime: new Date().getTime(),
        pauseStartTime: '',
        pauseTime: 0,
      });

      this.newTimer = '';
      timersStorage.saveTimers(this.timers);
    },
    deleteTimer(timerItem) {
      this.timers.splice(this.timers.indexOf(timerItem), 1);
    },
  },
  watch: {
    timers: {
      handler(timers) {
        timersStorage.saveTimers(timers);
      },
      deep: true,
    },
  },
};
</script>

<style scoped lang="scss">
  .timers-container {
    background: #fff;
    box-shadow: 0 1px 3px rgba(32, 33, 39, 0.12);
    border-radius: 12px;
    padding: 40px 0;
    @media screen and (max-width: 767px) {
      padding: 40px 15px;
    }
  }
  input {
    width: 305px;
    background: #F8F9FA;
    border: 1px solid #E7E8EA;
    border-radius: 6px;
    padding: 14px 20px;
    margin-right: 20px;
    outline: 0 transparent;
    @media screen and (max-width: 767px) {
      width: 100%;
      margin: 0 0 15px;
    }
    &:focus {
      border-color: #469AF4;
      &::-webkit-input-placeholder {
        color: transparent
      }
      &::-moz-placeholder {
        color: transparent
      }
      &:-moz-placeholder {
        color: transparent
      }
      &:-ms-input-placeholder {
        color: transparent
      }
    }
    &[placeholder] {
      font-size: 17px;
      line-height: 23px;
      color: rgba(103, 108, 117, 0.7);
      text-overflow:ellipsis;
    }
    &::-webkit-input-placeholder {
      font-size: 17px;
      line-height: 23px;
      color: rgba(103, 108, 117, 0.7);
      text-overflow:ellipsis;
    }
    &::-moz-placeholder {
      font-size: 17px;
      line-height: 23px;
      color: rgba(103, 108, 117, 0.7);
      text-overflow:ellipsis;
    }
    &:-moz-placeholder {
      font-size: 17px;
      line-height: 23px;
      color: rgba(103, 108, 117, 0.7);
      text-overflow:ellipsis;
    }
    &:-ms-input-placeholder {
      font-size: 17px;
      line-height: 23px;
      color: rgba(103, 108, 117, 0.7);
      text-overflow:ellipsis;
    }
  }
  .create-timer {
    font-weight: bold;
    font-size: 17px;
    line-height: 24px;
    text-align: center;
    letter-spacing: 1px;
    color: #FFFFFF;
    padding: 15px 25px 11px;
    box-shadow: 0 6px 12px rgba(40, 43, 49, 0.08);
    background: linear-gradient(163.14deg, #FF8E64 0%, #FFE641 100%);
    border-radius: 6px;
    @media screen and (max-width: 767px) {
      width: 100%;
    }
    &-container {
      padding: 0 0 27px;
      border-bottom: 1px solid #E7E8EA;
    }
    &-wrap {
      max-width: 490px;
      margin: 0 auto;
    }
  }
  .timers-list {
    padding: 30px 0 0;
    @media screen and (max-width: 399px) {
      padding: 0;
    }
  }
  .list-empty {
    text-align: center;
  }
</style>
