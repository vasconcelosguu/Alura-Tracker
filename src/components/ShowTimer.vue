<template>
  <section>
    <strong class="timer">{{ timeSeted }}</strong>
    </section>
</template>

<script lang="js">
  import { defineComponent } from 'vue';
  export default defineComponent({
    name: 'ShowTimer',
    props: {
      timer: {
        type: Number,
        default: 0,
      }
    },
    computed: {
    timeSeted () {
      return new Date(this.timer * 1000).toISOString().substring(11, 19)
    }
  }, 
  })
</script>
<style>
.timer {
  color: var(--text-primary);
}
</style>