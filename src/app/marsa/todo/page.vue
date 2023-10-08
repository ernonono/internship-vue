<script setup lang="ts">
import { ref } from 'vue';

const todos = ref<string[]>([])

const input = ref('')
const activeTab = ref('todo')

const onAddTodo = () => {
  todos.value.push(input.value)
  activeTab.value = 'done'
  input.value = ''
}
</script>
<template>
  <n-space justify="center" class="box">
    <n-card>
      <n-tabs type="line" animated class="tabel" v-model:value="activeTab">
        <n-tab-pane name="todo" tab="To Do">
          <n-form @submit.prevent="onAddTodo">
            <n-input v-model:value="input" class="inp-todo" type="text" placeholder="To Do Today..."></n-input>
            <n-space>
              <n-button attr-type="submit" class="button-add" type="primary" size="small"> Add To Do</n-button>
            </n-space>
          </n-form>
        </n-tab-pane>
        <n-tab-pane name="done" tab="Done">
          <n-list hoverable>
            <n-list item>
              <div class="py-4">
            <n-list hoverable>
              <template v-if="todos.length === 0">
               <n-text>nothing to do today</n-text>
              </template>
              <n-list-item v-for="(todo, i) in todos" :key="i" hoverable>
                {{ todo }}
              </n-list-item>
            </n-list>
          </div>
            </n-list>
          </n-list>
        </n-tab-pane>
      </n-tabs>
    </n-card>
  </n-space>

</template>

<style>
.box {
  
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}


.button-add{
  margin-top: 10px;
}
</style>