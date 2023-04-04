<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <ShowTimer :timer="timer" />
    <button class="button" @click="start" :disabled="setDisable">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finish" :disabled="!setDisable">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>
<script lang="js">
import { defineComponent } from 'vue';
import ShowTimer from './ShowTimer.vue'

export default defineComponent({
  name: 'FormsTimer',
  emites: ['stopTimer'],
  components: {
    ShowTimer
  },
  data () {
    return {
      timer: 0,
      localTimer: 0,
      setDisable: false,
    }
  },

  methods: {
    start () {
      this.localTimer = setInterval(() => {this.timer += 1}, 1000)
      this.setDisable = true
    },

    finish () {
      clearInterval(this.localTimer)
      this.setDisable = false
      this.$emit('stopTimer', this.timer)
      this.timer = 0
    }
  }
})</script>
