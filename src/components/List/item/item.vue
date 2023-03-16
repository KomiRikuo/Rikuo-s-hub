<script setup lang="ts">
import {defineProps} from "vue";

const props = defineProps<{
  removeTodoById:(uid:string)=>void
  id:string,
  changeTodoState:(uid:string)=>void
  content:string,
  state:boolean
}>()

const changeState =()=>{
 props.changeTodoState(props.id)
}
const removeTodo =()=>{
  props.removeTodoById(props.id)
}
</script>

<template>
<p>
    <input type="checkbox" :checked="state" @change="changeState"/>
  <span :class="{completed:state}"> {{props.content}}</span>
  <button v-if="state" @click="removeTodo">Remove</button>
</p>
</template>

<style scoped lang="scss">
.completed {
  text-decoration: line-through;
}
</style>
