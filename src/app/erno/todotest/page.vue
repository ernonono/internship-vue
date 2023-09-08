<route lang="yaml">
  meta:
    layout: guest
</route>

<script setup lang="ts"> 
import { onActivated, ref } from 'vue';
const todos = ref<string[]>([''])

const input = ref<string>('')
const activeTab = ref<string>('create')

const onAddTodo = (): void => {
  todos.value.push(input.value)
  activeTab.value = 'Todo'
  input.value = ''
}
// // const todos=ref;
// const todo = ref([]);
</script>

<template>
<n-space justify="center">
<n-card>
  <h1>Todo List</h1>
      <n-tabs 
      v-model:value="activeTab"
      animated>
      <n-tab-pane name="tambahtodo" tab="Tambah Todo">
        <n-form @submit.prevent="onAddTodo">
          <n-form-item label="Todo" path="Todo">
            <n-input  placeholder="Please Input" v-model:value="input">
            </n-input>
          </n-form-item>
        <n-space justify="left">
          <n-button attr-type="submit" type="primary"> 
          Submit
          </n-button>
        </n-space>
      </n-form>
      </n-tab-pane>
      <n-tab-pane name="Todo" tab="Todo">
    <n-list hoverable>
      <n-space vertical align="center">
      <n-empty description="Belum ada todo"/>
        <n-button type="primary" > 
          Tambah Todo 
        </n-button>
      </n-space>
     
        
        <n-list-item v-for="(todo, i) in todos" :key="i" hoverable>
          {{ todo }}
        </n-list-item>
    </n-list>
      </n-tab-pane>
    </n-tabs>
 

</n-card>
</n-space>


</template>

<style scoped>
  .n-card {
    width: 500px;
    margin-top: 300px;
  }
  </style>