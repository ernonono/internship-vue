<script setup lang="ts">
const todos = ref<string[]>([])

const input = ref('')
const activeTab = ref('create')
const currentTab = ref<'edit' | 'show'>('show')
const currentId = ref<number | null>(null)

const onAddTodo = () => {
  todos.value.push(input.value)
  activeTab.value = 'list'
  input.value = ''
}
</script>

<template>
  <div class="w-full min-h-screen flex justify-center items-center">
    <n-card class="max-w-lg">
      <n-tabs v-model:value="activeTab">
        <n-tab-pane name="create" tab="Tambah Todo">
          <div class="py-4">
            <n-form @submit.prevent="onAddTodo">
              <n-form-item label="Todo">
                <n-input v-model:value="input" />
              </n-form-item>
              <n-button attr-type="submit" type="primary"> Add </n-button>
            </n-form>
          </div>
        </n-tab-pane>
        <n-tab-pane name="list" tab="Todo">
          <div class="py-4">
            <n-list hoverable>
              <template v-if="todos.length === 0">
                <n-empty description="Belum ada todo">
                  <template #extra>
                    <n-button type="primary"> Tambah Todo </n-button>
                  </template>
                </n-empty>
              </template>
              <n-list-item v-for="(todo, i) in todos" :key="i" hoverable>
                <div v-if="i === currentId && currentTab === 'edit'">
                  <n-input v-model:value="todos[i]"></n-input>
                </div>
                <template v-else>{{ todo }}</template>
                <template #suffix>
                  <n-button
                    v-if="currentTab === 'show'"
                    @click="
                      () => {
                        currentTab = 'edit'
                        currentId = i
                      }
                    "
                  >
                    Edit
                  </n-button>
                  <n-button v-else @click="currentTab = 'show'">Cancel</n-button>
                </template>
              </n-list-item>
            </n-list>
          </div>
        </n-tab-pane>
      </n-tabs>
    </n-card>
  </div>
</template>
