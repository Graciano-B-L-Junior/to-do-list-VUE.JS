<template>
  <div>
    <div class="inputTask">
      <input
        type="text"
        id="input"
        placeholder="Nova tarefa?"
        v-model="ativ"
        
      />
      <button @click="adicionarAtividade()">+</button>
    </div>
  </div>
</template>

<script>
import Barramento from "../barramento.js";
export default {
  props: {
    addAtividade: { type: Function, required: true },
  },
  data() {
    return {
      ativ: "",
    };
  },
  methods: {
    
    adicionarAtividade() {
      if (this.ativ != "" || !this.ativ.isEmpty) {
        this.addAtividade(this.ativ)
        this.ativ=''
      }
    },
  },
};
</script>

<style scoped>
.inputTask {
  margin-top: 25px;
  width: 300px;
  height: 35px;
  display: flex;
  justify-content: center;
  border: 1px solid #ccc;
  border-radius: 5px;
}
input {
  border: none;
  outline: none;
  background-color: rgba(0, 0, 0, 0);
  color: white;
  display: inline-block;
  flex-grow: 10;
  padding: 5px;
  margin: 0;
}
button {
  flex-grow: 1;
  border: none;
  background-color: rgb(79, 130, 241);
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
  color: white;
  cursor: pointer;
}
</style>