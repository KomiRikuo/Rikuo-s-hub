<script setup lang="ts">
import {ITodo} from "../../typings";
import {defineProps} from "vue";
import Item from "./item/item.vue";

const props = defineProps<{
  userTodoListRef: ITodo[]
  removeTodoById:(uid:string) => void
  changeTodoState:(uid:string) => void
}>()
</script>

<template>
  <item v-for="item in props.userTodoListRef"
        :id ="item.id"
        :content="item.content"
        :state = "item.state"
        :remove-todo-by-id ="props.removeTodoById"
        :change-todo-state = "props.changeTodoState"
        :key ="item.id"/>
</template>
