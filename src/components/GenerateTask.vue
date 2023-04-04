<template>
  <RenderBox>
    <div class="columns">
      <div class="column is-7">{{ task.description || 'Tarefa sem descrição' }}</div>
      <div class="column">
        <ShowTimer :timer="task.time" />
      </div>
    </div>
  </RenderBox>
</template>
<script lang="js">
import { defineComponent } from 'vue'
import ShowTimer from './ShowTimer.vue';
import RenderBox from './RenderBox.vue';


export default defineComponent({
  name: "GenerateTask",
  props: {
    task: {
      type: Object,
      required: true,
    }
  },
  components: {
    ShowTimer,
    RenderBox
  }
})
</script>
