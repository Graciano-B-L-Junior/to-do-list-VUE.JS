<template>
  <div id="app">
    <h1>Tarefas</h1>
    <ProgressionBar />
    <InputTask />
    <div class="atividades">
      <template v-for="n in 10">
        <task :atividade="'ola'" :key="n" />
      </template>
    </div>
  </div>
</template>

<script>
import ProgressionBar from "./components/ProgressionBar.vue";
import InputTask from "./components/InputTask.vue";
import Task from "./components/Task.vue";
export default {
  components: {
    ProgressionBar,
    InputTask,
    Task,
  },
};
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
.atividades{
	display: flex;
	flex-wrap: wrap;
}
</style>
