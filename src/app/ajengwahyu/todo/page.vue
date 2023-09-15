<script setup lang="ts">
import { ref } from 'vue'
import {
  CheckmarkCircleOutline,
  CloseCircleOutline,
  PencilOutline,
  TrashOutline
} from '@vicons/ionicons5'

const todos = ref<string[]>([])
const inputTodo = ref('')
const activeTab = ref('todo')
const currentTab = ref<'edit' | 'show'>('show')
const currentId = ref<number | null>(null)
const originalTodoValue = ref('')

const tambahTodo = () => {
  todos.value.push(inputTodo.value)
  activeTab.value = 'list'
  inputTodo.value = ''
}

const editTodo = (index: number) => {
  originalTodoValue.value = todos.value[index]
  currentTab.value = 'edit'
  currentId.value = index
  inputTodo.value = todos.value[index]
}

const saveTodo = (index: number) => {
  currentTab.value = 'show'
  currentId.value = null
  inputTodo.value = ''
}

const cancelTodo = (index: number) => {
  if (currentId.value !== null && currentTab.value === 'edit') {
    todos.value[currentId.value] = originalTodoValue.value
    currentTab.value = 'show'
    currentId.value = null
    inputTodo.value = ''
  }
}

const handleClick = () => {
  activeTab.value = 'todo'
}

const deleteTodo = (index: number) => {
  todos.value.splice(index, 1)
}
</script>

<template>
  <div class="w-full min-h-screen flex justify-center items-center">
    <n-space justify="center">
      <n-card style="width: 500px">
        <n-tabs v-model:value="activeTab">
          <n-tab-pane name="todo" tab="Tambah">
            <n-form @submit.prevent="tambahTodo">
              <n-form-item path="todo" label="Todo">
                <n-input v-model:value="inputTodo" type="text" placeholder="Masukkan todo" />
              </n-form-item>
              <n-button attr-type="submit" type="primary"> Tambah </n-button>
            </n-form>
          </n-tab-pane>
          <n-tab-pane name="list" tab="List">
            <n-list hoverable>
              <template v-if="todos.length === 0">
                <n-empty description="Belum ada todo">
                  <template #extra>
                    <n-button type="primary" @click="handleClick()"> Tambah </n-button>
                  </template>
                </n-empty>
              </template>
              <n-list-item v-for="(todo, i) in todos" :key="i" hoverable>
                <div>
                  <div v-if="i === currentId && currentTab === 'edit'">
                    <div style="display: flex; align-items: center">
                      <n-input v-model:value="todos[i]" style="flex-grow: 1"></n-input>
                      <n-space justify="end">
                        <n-button @click="() => saveTodo(i)" strong secondary type="primary">
                          <n-icon size="20">
                            <checkmark-circle-outline />
                          </n-icon>
                        </n-button>
                        <n-button @click="() => cancelTodo(i)" strong secondary type="error"
                          ><n-icon size="20"> <close-circle-outline /> </n-icon
                        ></n-button>
                      </n-space>
                    </div>
                  </div>
                  <div v-else>
                    <div style="display: flex; align-items: center">
                      <span style="flex-grow: 1">{{ todo }}</span>
                      <n-space justify="end">
                        <n-button
                          v-if="currentTab === 'show'"
                          @click="editTodo(i)"
                          secondary
                          type="warning"
                          ><n-icon size="20">
                            <pencil-outline />
                          </n-icon>
                        </n-button>
                        <n-button @click="deleteTodo(i)" strong secondary type="error"
                          ><n-icon size="20"> <trash-outline /> </n-icon
                        ></n-button>
                      </n-space>
                    </div>
                  </div>
                </div>
              </n-list-item>
            </n-list>
          </n-tab-pane>
        </n-tabs>
      </n-card>
    </n-space>
  </div>
</template>
