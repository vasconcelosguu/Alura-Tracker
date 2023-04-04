<template>
  <main class="columns is-gapless is-multiline" :class="{'dark-mode':darkMode}">
    <div class="column is-one-quarter">
      <SideBar @setTheme="changeTheme"/>
    </div>
    <div class="column is-three-quarter content">
      <FormsTask @onSaveTask="saveTask" />
      <div class="lista">
        <GenerateTask :task="task" v-for="(task, i) in tasks" :key="i" />
        <RenderBox v-if="emptyTasks"> Você ainda não criou nenhuma tarefa 😿 </RenderBox>
      </div>
    </div>
  </main>
</template>

<script>
import SideBar from "./components/SideBar.vue";
import FormsTask from "./components/Forms.vue";
import GenerateTask from "./components/GenerateTask.vue";
import RenderBox from "./components/RenderBox.vue";

export default {
  name: "App",
  components: {
    SideBar,
    FormsTask,
    GenerateTask,
    RenderBox,
  },

  data() {
    return {
      tasks: [],
      darkMode: false,
    };
  },

  computed: {
    emptyTasks() {
      return this.tasks.length === 0;
    },
  },

  methods: {
    saveTask(task) {
      this.tasks.push(task);
    },
    changeTheme (darkMode) {
      this.darkMode = darkMode
    }
  },
};
</script>

<style>
.lista {
  padding: 1.25rem;
}
main {
  --bg-primary: white;
  --text-primary: black;
}
main.dark-mode {
  --bg-primary: rgb(61, 60, 60);
  --text-primary: rgb(210, 210, 215);
}
.content {
  background-color: var(--bg-primary);
}
</style>
