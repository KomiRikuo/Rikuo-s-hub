<script setup lang="ts">
import {ref,watch} from "vue";
import type {Ref} from "vue";
import type {ITodo} from "../../typings";
import {nanoid} from "nanoid"

const props = defineProps<{
  addTodoThings:(userTodoThingsObject:ITodo)=>void
}>()

const userInputRef:Ref<string> = ref("")
const addTodo = ():void =>{
  if (userInputRef.value.trim().length > 0 ){
    const userTodoThingsObject:ITodo ={
      id:nanoid(),
      content:userInputRef.value.trim(),
      state:false
    }
    props.addTodoThings(userTodoThingsObject)
    return
  }
  alert("enter click")
}
</script>

<template>
  <input type="text" placeholder="Please add todo things" v-model="userInputRef"/>
  <button @click="addTodo">Add</button>
</template>

<style scoped>

</style>