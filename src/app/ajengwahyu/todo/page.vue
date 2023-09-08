<script setup lang="ts">
import {ref} from 'vue'

const todos = ref<string[]>([])
const inputTodo = ref('')
const activeTab = ref('todo')

const tambahTodo = () => {
  todos.value.push(inputTodo.value)
  activeTab.value = 'list'
  inputTodo.value = ''
}

const handleClick = () => {
    activeTab.value = 'todo'
}
</script>

<template>
  <div class="w-full min-h-screen flex justify-center items-center">
    <n-space justify="center">
      <n-card :class="$style.card">
        <n-tabs v-model:value="activeTab">
          <n-tab-pane name="todo" tab="Tambah">
            <n-form @submit.prevent="tambahTodo">
              <n-form-item path="todo" label="Todo">
                <n-input v-model:value="inputTodo" type="text" placeholder="Masukkan todo" />
              </n-form-item>
              <n-button attr-type="submit" type="primary"> Tambah </n-button>
            </n-form>
          </n-tab-pane> giy
          <n-tab-pane name="list" tab="List">
            <n-list hoverable>
              <template v-if="todos.length === 0">
                <n-empty description="Belum ada todo">
                  <template #extra>
                    <n-button type="primary" @click="handleClick"> Tambah </n-button>
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
    </n-space>
  </div>
</template>

<style scoped module>
.card {
  width: 500px;
}
</style>
