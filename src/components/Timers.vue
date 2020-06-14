<template>
  <div class="timers-container">
    <div class="create-timer-container">
      <input type="text" placeholder="Timer Name">
      <button type="button" class="create-timer">Create Timer</button>
    </div>
    <div class="timers-list">
      <div class="timer-item">
        <span class="name">Timer name 1</span>
        <span class="time">00:00:35</span>
        <button class="btn-pause">
          <i class="mdi mdi-pause"></i>
        </button>
        <button class="btn-delete">
          <i class="mdi mdi-delete"></i>
        </button>
      </div>
      <div class="timer-item">
        <span class="name">Timer name 2</span>
        <span class="time">00:00:47</span>
        <button class="btn-pause">
          <i class="mdi mdi-pause"></i>
        </button>
        <button class="btn-delete">
          <i class="mdi mdi-delete"></i>
        </button>
      </div>
      <div class="timer-item">
        <span class="name">Timer name 3</span>
        <span class="time">00:01:49</span>
        <button class="btn-play">
          <i class="mdi mdi-play"></i>
        </button>
        <button class="btn-delete">
          <i class="mdi mdi-delete"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Timers',
};
</script>

<style scoped lang="scss">
  .timers-container {
    background: #fff;
    box-shadow: 0 1px 3px rgba(32, 33, 39, 0.12);
    border-radius: 12px;
    padding: 40px 0;
  }
  input {
    width: 305px;
    background: #F8F9FA;
    border: 1px solid #E7E8EA;
    border-radius: 6px;
    padding: 14px 20px;
    margin-right: 20px;
    outline: 0 transparent;
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
    &-container {
      padding: 0 140px 27px;
      border-bottom: 1px solid #E7E8EA;
    }
  }
  .timers-list {
    padding: 30px 140px 0;
  }
  .timer-item {
    display: flex;
    align-items: center;
    padding-bottom: 39px;
    &:last-of-type {
      padding-bottom: 0;
    }
    .name {
      font-weight: 800;
      font-size: 20px;
      line-height: 30px;
      color: #5586F2;
      margin-right: 58px;
    }
    .time {
      font-size: 17px;
      line-height: 23px;
      color: #676C75;
      background: #E7E8EA;
      border: 1px solid #E7E8EA;
      border-radius: 6px;
      padding: 13px 24px;
      margin-right: 41px;
    }
    button {
      width: 50px;
      height: 50px;
      color: #fff;
      box-shadow: 0 6px 12px rgba(40, 43, 49, 0.08);
      margin-right: 20px;
      i {
        font-size: 150%;
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
