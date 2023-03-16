<script setup lang="ts">
import Header from "./components/Header/Header.vue"
import List from "./components/List/List.vue"
import Footer from "./components/Footer/Footer.vue"
import {onMounted, ref, watch} from "vue";
import type {Ref} from "vue";
import type {ITodo} from"./typings";

const userTodoListRef:Ref<ITodo[]>=ref([])
const addTodoThings = (userInputTodoObject:ITodo):void=>{
  userTodoListRef.value.push(userInputTodoObject)
}

const changeTodoState = (uid:string) =>{
  userTodoListRef.value.forEach((todo:ITodo)=>{
    if (todo.id === uid){
      todo.state =! todo.state
    }
  })
}

const removeTodoById = (uid:string):void =>{
  userTodoListRef.value = userTodoListRef.value.filter((todo:ITodo)=>{
    return todo.id != uid
  })
}

watch<Ref<ITodo[]>>(userTodoListRef,()=>{
  localStorage.setItem("todoList",JSON.stringify(userTodoListRef.value))
},{
  deep:true
})

onMounted(()=>{
  const objectSet:ITodo[] = JSON
})


</script>

<template>
    <Header :addTodoThings="addTodoThings"/>
    <List :userTodoListRef="userTodoListRef" :changeTodoState="changeTodoState" :removeTodoById="removeTodoById"/>
    <Footer :userTodoListRef="userTodoListRef"/>
</template>

