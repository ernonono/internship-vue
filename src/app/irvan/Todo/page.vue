<route lang="yaml">
  meta:
    layout: guest
  </route>

<script setup lang="ts"> 
import { ref } from 'vue';
const todos = ref<string[]>(['rtrt'])

const input = ref<string>('')
const activeTab = ref<string>('create')

const onAddTodo = (): void => {
  todos.value.push(input.value)
  activeTab.value = 'ToDo Hari Ini'
  input.value = ''
}
// // const todos=ref;
// const todo = ref([]);
</script>

<template>

<n-card title="ToDolist" style="margin-bottom: 16px">
    <n-tabs type="line" animated v-model:value="activeTab">
      <n-tab-pane name="oasis" tab="ToDo">
        <n-form @submit.prevent="onAddTodo">
        <n-text>Silahkan Masukkan List</n-text>
        <br>
        <br>
        <n-form-item label="ToDo" path="ToDo" label-width="50">
          <n-input type="text" placeholder="Silahkan Input" v-model:value="input">
          </n-input>
        </n-form-item>
        <n-button attr-type="submit" type="primary">
          Submit
        </n-button>
        </n-form>
      </n-tab-pane>
      <n-tab-pane name="ToDo Hari Ini" tab="ToDo Hari Ini">
        <n-list hoverable>
              <template v-if="todos.length === 0">
                <n-empty description="Belum ada todo">
                  <template #extra>
                    <n-button type="primary"> Tambah Todo </n-button>
                  </template>
                </n-empty>
              </template>
              <n-list-item v-for="(todo, i) in todos" :key="i" hoverable>
                {{ todo }}
              </n-list-item>
            </n-list>
      </n-tab-pane>
    </n-tabs>
  </n-card>
</template>

<style scoped>
.n-card {
  background-color: theme('colors.white');
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  width: 600px;
  margin-top: 50px;
  margin-left: 450px;
}
</style>