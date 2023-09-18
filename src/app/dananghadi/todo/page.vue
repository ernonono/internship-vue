<<<<<<< HEAD
<script setup lang="ts">
import { ref } from 'vue'
import { TrashOutline, Pencil, Save, Close } from '@vicons/ionicons5'

const todos = ref<string[]>([])
const inputtodo = ref('')
const activeTab = ref('todo')
const currentTab = ref<'edit' | 'show'>('show')
const currentId = ref<number | null>(null)
const originalTodoValue = ref('')

const Add = () => {
  todos.value.push(inputtodo.value)
  activeTab.value = 'list'
  inputtodo.value = ''
}

const Edittodo = (index: number) => {
  originalTodoValue.value = todos.value[index]
  currentTab.value = 'edit'
  currentId.value = index
  inputtodo.value = todos.value[index]
}

const saveEdit = (index: number) => {
  currentTab.value = 'show'
  currentId.value = null
  inputtodo.value = ''
}

const cancelEdit = (index: number) => {
  if (currentId.value !== null && currentTab.value === 'edit') {
    todos.value[currentId.value] = originalTodoValue.value
    currentTab.value = 'show'
    currentId.value = null
    inputtodo.value = ''
  }
}
const removeTodo = (index: number) => {
  todos.value.splice(index, 1)
}

const Addtodo = () => {
  activeTab.value = 'todo'
}
</script>

<template>
  <div class="w-full min-h-screen flex justify-center items-center">
    <n-card :class="$style.logincard" title="TODO">
      <n-tabs
        class="card-tabs"
        v-model:value="activeTab"
        default-value="add"
        size="large"
        animated
        pane-wrapper-style="margin: 0 -4px"
        pane-style="padding-left: 4px; padding-right: 4px; box-sizing: border-box; padding-top: 2px;"
      >
        <n-tab-pane name="todo" tab="Add">
          <n-form @submit.prevent="Add">
            <n-form-item-row>
              <n-input v-model:value="inputtodo" placeholder="Input TODO" />
            </n-form-item-row>
            <n-button attr-type="submit" type="primary" block secondary strong> Add </n-button>
          </n-form>
        </n-tab-pane>
        <n-tab-pane name="list" tab="List">
          <n-list hoverable>
            <template v-if="todos.length === 0">
              <n-empty description="No todos">
                <template #extra>
                  <n-button type="primary" @click="Addtodo"> Add Todo </n-button>
                </template>
              </n-empty>
            </template>
            <n-list-item v-for="(todo, i) in todos" :key="i" hoverable>
              <div>
                <div v-if="i === currentId && currentTab === 'edit'">
                  <div style="display: flex; align-items: center">
                    <n-input v-model:value="todos[i]" style="flex-grow: 1"></n-input>
                    <div class="flex space-x-2">
                      <n-button
                        style="margin-left: 4px"
                        @click="() => saveEdit(i)"
                        strong
                        secondary
                        type="primary"
                      >
                        <n-icon size="20">
                          <Save />
                        </n-icon>
                      </n-button>
                      <n-button @click="() => cancelEdit(i)" strong secondary type="error">
                        <n-icon size="20"> <Close /> </n-icon>
                      </n-button>
                    </div>
                  </div>
                </div>
                <div v-else>
                  <div style="display: flex; align-items: center">
                    <span style="flex-grow: 1">{{ todo }}</span>
                    <n-space justify="end">
                      <n-button
                        v-if="currentTab === 'show'"
                        @click="Edittodo(i)"
                        strong
                        secondary
                        type="warning"
                      >
                        <n-icon size="20">
                          <Pencil />
                        </n-icon>
                      </n-button>
                      <n-button @click="removeTodo(i)" strong secondary type="error">
                        <n-icon size="20"> <TrashOutline /> </n-icon>
                      </n-button>
                    </n-space>
                  </div>
                </div>
              </div>
            </n-list-item>
          </n-list>
        </n-tab-pane>
      </n-tabs>
    </n-card>
  </div>
</template>
<style scoped module>
.logincard {
  width: 500px;
  background-color: theme('colors.white');
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  font-family: Century Gothic;
}
</style>
=======
<script setup lang="ts">
import { ref } from 'vue'

const todos = ref<string[]>([])

const inputtodo = ref('')
const activeTab = ref('todo')

const Add = () => {
  todos.value.push(inputtodo.value)
  activeTab.value = 'list'
  inputtodo.value = ''
}
const Addtodo = () => {
  activeTab.value = 'todo'
}
const removeTodo = (index: number) => {
  todos.value.splice(index, 1)
}
</script>
<template>
  <div class="w-full min-h-screen flex justify-center items-center">
    <n-card :class="$style.logincard" title="TODO">
      <n-tabs
        class="card-tabs"
        v-model:value="activeTab"
        default-value="add"
        size="large"
        animated
        pane-wrapper-style="margin: 0 -4px"
        pane-style="padding-left: 4px; padding-right: 4px; box-sizing: border-box;"
      >
        <n-tab-pane name="todo" tab="Add">
          <n-form @submit.prevent="Add">
            <n-form-item-row>
              <n-input v-model:value="inputtodo" placeholder="Input TODO" />
            </n-form-item-row>
            <n-button attr-type="submit" type="primary" block secondary strong> Add </n-button>
          </n-form>
        </n-tab-pane>
        <n-tab-pane name="list" tab="List">
          <div class="py-4">
            <n-list hoverable>
              <template v-if="todos.length === 0">
                <n-empty description="No todos">
                  <template #extra>
                    <n-button type="primary" @click="Addtodo"> Add Todo </n-button>
                  </template>
                </n-empty>
              </template>
              <n-list-item v-for="(todo, i) in todos" :key="i" hoverable>
                {{ todo }}
                <n-button type="error" size="small" style="float: right" @click="removeTodo(i)">Delete
                </n-button>
              </n-list-item>
            </n-list>
          </div>
        </n-tab-pane>
      </n-tabs>
    </n-card>
  </div>
</template>
<style scoped module>
.card-tabs .n-tabs-nav--bar-type {
  padding-left: 4px;
}
.logincard {
  width: 500px;
  background-color: theme('colors.white');
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  font-family: Century Gothic;
}
</style>
>>>>>>> 4194e38 (fix: vue query)
