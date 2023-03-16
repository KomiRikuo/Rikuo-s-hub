<script setup lang="ts">
import {computed} from "vue";
import type {ComputedRef} from "vue";
import {ITodo} from "../../typings";

const props = defineProps<{
  userTodoListRef:ITodo[]
}>()

const isTrueStateRef: ComputedRef<number> = computed(()=>{
  return props.userTodoListRef.reduce((pre:number,curr:ITodo)=>{
    return pre += (curr.state === true ? 1 : 0)
  },0)
})
</script>

<template>
  <p>Total:{{isTrueStateRef}}</p>
</template>
