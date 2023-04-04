
<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="logo">
    </h1>
    <button class="button" @click="changeTheme">
      {{ textInput }}
    </button>
  </header>
</template>

<script lang="js">
import { defineComponent } from 'vue';
export default defineComponent({
  name:  'SideBar',
  emits: ['setTheme'],
  data () {
    return {
      darkModeOn: false,
    }
  },
  computed: {
    textInput () {
      if (this.darkModeOn) return  'Set Light Mode'
      return 'Set Dark Mode'
    },
  },
  methods: {
  changeTheme() {
    this.darkModeOn = !this.darkModeOn
    this.$emit('setTheme', this.darkModeOn)
  },  
},
},

  )
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>