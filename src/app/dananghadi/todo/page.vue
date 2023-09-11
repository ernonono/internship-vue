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
