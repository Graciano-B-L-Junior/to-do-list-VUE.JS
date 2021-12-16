<template>
  <div
    @click="TaskClicada()"
    :style="{ backgroundColor: backgroundBackColor }"
    class="task-box"
  >
    <div
      class="task-box-content"
      :style="{ backgroundColor: backgroundFrontColor }"
    >
      <button @click="DeleteTask(atividade)">X</button>
      <p :style="{ textDecoration: textDecoration }">{{ atividade.atividade }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    atividade: {
      type: Object,
      required: true,
    },
    DeleteTask:{
      type: Function
    },
    AtualizaPorcentagem:{
      type: Function
    }
  },
  data() {
    return {
      taskConcluida: false,
      backgroundBackColor: "rgb(75, 1, 1)",
      backgroundFrontColor: "rgb(155, 0, 0)",
      textDecoration: "none",
    };
  },

  methods: {
    TaskClicada() {
      if (this.taskConcluida) {
        this.TaskDesmarcada();
      } else {
        this.TaskMarcada();
      }
      this.AtualizaPorcentagem()
    },
    TaskMarcada() {
      this.taskConcluida = true;
      this.atividade.concluido=true
      this.backgroundBackColor = "rgb(1, 75, 50)",
      this.backgroundFrontColor = "rgb(0, 155, 103)";
      this.textDecoration = "line-through";
    },
    TaskDesmarcada() {
      this.taskConcluida = false;
      this.backgroundBackColor = "rgb(75, 1, 1)";
      this.backgroundFrontColor = "rgb(155, 0, 0)";
      this.textDecoration = "none";
      this.atividade.concluido=false
    },
    
  },
};
</script>

<style scoped>
.task-box {
  margin-top: 30px;
  margin-left: 10px;
  margin-right: 10px;
  height: 90px;
  width: 200px;
  background-color: rgb(75, 1, 1);
  border-radius: 10px;
  display: flex;
  flex-direction: row-reverse;
}
.task-box-content {
  width: 96%;
  height: 100%;
  background-color: rgb(155, 0, 0);
  display: flex;
  align-items: center;
  box-sizing: border-box;
  padding-left: 30px;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
  cursor: pointer;
}
button {
  position: relative;
  top: -30px;
  left: 135px;
  border: none;
  background-color: rgba(0, 0, 0, 0.644);
  height: 20px;
  width: 20px;
  border-radius: 10px;
  color: white;
  cursor: pointer;
}
</style>