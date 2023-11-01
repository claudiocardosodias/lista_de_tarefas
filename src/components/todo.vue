<script setup>
import {   ref } from 'vue'
import ContagemTask from './ContagemTask.vue';
 
//alert box
import { toast } from 'vue3-toastify';
import 'vue3-toastify/dist/index.css';


toast('Seja bem vindo ao TodoList', {
  autoClose: 300,
});
 
 
////fim dos alertas

const tarefas = ref([]);
const inputValue = ref("");

 function addTask(){
      if(inputValue.value != ""){
        
        tarefas.value.push(inputValue.value);
         
        inputValue.value ="";
        toast.success("Tarefa Adicionada!" , {
          autoClose: 500,
        })
      }else{
        
        alert("insira algo")
      }
    
 }
function deleteTask(index){
  tarefas.value.splice(index, 1)
  toast.warning("Tarefa removida!" , {
    
    autoClose: 300,
  })
}
 
</script>

<template>
  
  <div>
    <h1 class="todo">Todo List</h1>
    <div class="card">
      <div class="contagem">
        <ContagemTask :count="tarefas.length" />
      </div>
      
      <div class="input-button">
        <input  v-model="inputValue" type="text" id="inputTask">
        <button type="button"  @click="addTask"><span class="material-symbols-outlined">
   add_box
</span> </button>
      </div>
    </div>
    <div class="tarefas">
      <ul class="task">
        
        <li v-for="tarefa  in tarefas" :key="tarefa">
          {{ tarefa }} 
          <button @click="deleteTask" class="remover"><span class="material-symbols-outlined " id="add" >
          delete
</span></button></li>
      </ul>
      
    </div>
    
  </div>
 
   
</template>

<style scoped> 

.todo {
  display: flex; justify-content: center
}
.card {
  position: relative;
  margin-top: 3rem;
  border-radius: 1rem;
  padding: 2rem;
  width: 600px;
  background-color: #242424;
  color: rgba(255, 255, 255, 0.87);
 
}

.input-button{
  margin-top: 1rem;
}
.card .input-button ,   input ,  button {
  display: flex;
  justify-content: space-around;
  align-items: center;  
 
}
 
.card .input-button  input {
   border-radius: 20px;
  width: 70%;
  outline: none;
  border-style: none;
  padding: 1rem;
   

}
 .tarefas{
   
  display: flex;
  justify-content: center;
  margin-top: 1rem;
 }

 
.tarefas  li{
  
  font-family: monospace;
  text-transform: uppercase;
  background-color: #242424;
  padding: 0.5rem;
 
  border-radius: 20px;
 color: #fff;
 display: flex;
 justify-content: center;
 align-items: center;
 gap: 1rem;
 margin-bottom: 0.5rem;
}

.remover {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2px;
  background-color: red;
  color: #fff;
  border-style: none;
  border-radius: 50%;
  cursor: pointer;
}
 
 .contagem {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: #fff;
  color: #242424;
  padding: 2px;
  border-radius: 1rem;
  text-transform: uppercase;
  
 }
 
.input-button button {
  background-color: rgb(0, 214, 0);
  border-style: none;
  padding: 0.5rem;
  border-radius: 100%;
  cursor:  pointer;
}
.input-button  span {
   
  color: #fff;
 }
</style>
