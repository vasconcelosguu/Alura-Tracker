<template>
  <div class="box forms">
    <div class="columns">
        <div
          class="column is-8"
          role="form"
          aria-label="Formulario Para cria tarefa"
        >
          <input
          type="text"
          class="input"
         placeholder="Qual a Nova Tarefa?"
         v-model="taskDescription"
         />
        </div>
        <div class="column">
          <FormsTimer @stopTimer="finishTak"/>
        </div>
    </div>
  </div>
</template>

<script lang="js">
import { defineComponent } from 'vue';
import FormsTimer from './FormsTimer.vue'

export default defineComponent({
  name: 'FormsTask',
  emits: ['onSaveTask'],
  components: {
    FormsTimer,
  },
  data () {
    return {
      taskDescription: '',
    }
  },
  methods: {
    finishTak (timer) {
      this.$emit('onSaveTask', {
        time: timer,
        description: this.taskDescription,
      })
      this.taskDescription = ''
    }
  }
})
</script>
<style>
.forms {
  background-color: var(--bg-primary);
  color: var(--text-primary);
  }
</style>
