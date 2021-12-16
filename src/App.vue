<template>
  <div id="app">
    <h1>Tarefas</h1>
    <ProgressionBar :progress="porcentagem" />
    <InputTask :addAtividade="adicionarAtividade" />
    <div class="atividades">
    <template v-for="(atividade,index) in lista">
      <Task :AtualizaPorcentagem="atualizaPorcentagem" :DeleteTask="removerAtividade" :atividade="atividade" :key="index"/>
    </template>
    </div>
  </div>
</template>

<script>
import ProgressionBar from "./components/ProgressionBar.vue";
import InputTask from "./components/InputTask.vue";
import Task from "./components/Task.vue";
import Barramento from './barramento.js'
export default {
  components: {
    ProgressionBar,
    InputTask,
    Task,
  },
  data(){
    return{
      lista:[],
      porcentagem:0
    }
  },
  methods:{
    adicionarAtividade(atv){
      if(!atv.isEmpty||ativ!=""){
        let atividade = {concluido:false,atividade:atv}
        this.lista.push(atividade)
        this.atualizaPorcentagem()
      }
    },
    removerAtividade(atv){
      let index = this.lista.indexOf(atv)
      this.lista.splice(index,1)
      this.atualizaPorcentagem()
    },
    atualizaPorcentagem(){
      let QtdAtividades = this.lista.length
      let QtdAtividadesFeitas=0
      this.lista.map(e=>{
        if(e.concluido==true){
          QtdAtividadesFeitas++
        }
      })
      this.porcentagem = (QtdAtividadesFeitas*100)/QtdAtividades
      this.porcentagem = parseInt(this.porcentagem,10)
    }
  }
  
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
