<template>
    <div>
        <div class="pb-10">🌺 🌸 🌺</div>
      <div class="text-center py-8" v-if="currentTime">
        <span v-if="days">
          Days: {{ days }}<br/>
        </span>
        <span v-if="hours">
          Hours: {{ hours | formatTime }} <br/>
        </span>
        Minutes: {{ minutes | formatTime }} <br/>
        Seconds: {{ seconds | formatTime }} <br/>

       </div>
      <div class="text-center" v-if="!currentTime && returnTime > 0">
        ❤️ On est en Colombie❤️
      </div>
      <div class="text-center" v-if="!currentTime && returnTime <= 0">
        💔 On rentre! 💔
      </div>
      <div class="pt-10">😎 💃🏾 🌞</div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      deadline: {
        type: String,
        required: true,
      },
    returnDeadline: {
        type: String,
        required: true,
      },
      speed: {
        type: Number,
        default: 1000,
      },
    },
    data() {
      return {
        currentTime: Date.parse(this.deadline) - Date.parse(new Date()),
        returnTime: Date.parse(this.returnDeadline) - Date.parse(new Date()),
      };
    },
    mounted() {
      setTimeout(this.countdown, 1000);
    },
    computed: {
      seconds() {
        return Math.floor((this.currentTime / 1000) % 60);
      },
      minutes() {
        return Math.floor((this.currentTime / 1000 / 60) % 60);
      },
      hours() {
        return Math.floor((this.currentTime / (1000 * 60 * 60)) % 24);
      },
      days() {
        return Math.floor(this.currentTime / (1000 * 60 * 60 * 24));
      }
    },
    filters: {
      formatTime(value) {
        if (value < 10) {
          return "0" + value;
        }
        return value;
      }
    },
    methods: {
      countdown() {
        this.currentTime = Date.parse(this.deadline) - Date.parse(new Date());
        if (this.currentTime > 0) {
          setTimeout(this.countdown, this.speed);
        } else {
          this.currentTime = null;
        }

        this.returnTime = Date.parse(this.deadline) - Date.parse(new Date());
        if (this.returnTime <= 0) {
          this.returnTime = null;
        }
      }
    }
  }
  </script>
