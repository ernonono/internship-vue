<script setup lang="ts">
import { Delete24Regular, CalendarEdit20Regular, CalendarCancel24Regular } from '@vicons/fluent'
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

const removeTodo = (index: number) => {
  todos.value.splice(index, 1)
}
</script>

<template>
  <n-space vertical>
    <n-card title="To do List" style="margin-bottom: 16px">
      <n-tabs type="segment" animated v-model:value="activeTab">
        <n-tab-pane name="create" tab="Todo">
          <n-form @submit.prevent="onAddTodo">
            <n-form-item label="Todo">
              <n-input
                v-model:value="input"
                class="size-Font"
                placeholder="Silahkan Input todo anda hari ini"
              />
            </n-form-item>
            <n-space justify="center">
              <n-button tertiary type="primary" attr-type="submit">Submit</n-button></n-space
            >
          </n-form>
        </n-tab-pane>
        <n-tab-pane name="list" tab="List Todo">
          <n-list hoverable>
            <template v-if="todos.length === 0">
              <n-empty description="Belum ada todo">
                <template #extra>
                  <n-button tertiary type="primary"> Tambah Todo </n-button>
                </template>
              </n-empty>
            </template>
            <n-list-item v-for="(todo, i) in todos" :key="i" hoverable>
              <n-space class="size-Font" justify="space-between">
                <div v-if="i === currentId && currentTab === 'edit'">
                  <n-input v-model:value="todos[i]"></n-input>
                </div>
                <template v-else>{{ todo }}</template>
                <n-space>
                  <n-button
                    class="custom-Button centered-Button"
                    @click="removeTodo(i)"
                    tertiary
                    type="error"
                  >
                    <n-icon size="20">
                      <delete24-regular />
                    </n-icon>
                    Hapus
                  </n-button>
                  <div>
                    <n-button
                      v-if="currentTab === 'show'"
                      class="custom-Button centered-Button"
                      @click="
                        () => {
                          currentTab = 'edit'
                          currentId = i
                        }
                      "
                      tertiary
                      type="info"
                    >
                      <n-icon size="20">
                        <calendar-edit20-regular />
                      </n-icon>
                      Edit
                    </n-button>
                    <n-button
                      v-else
                      class="custom-Button centered-Button"
                      @click="currentTab = 'show'"
                      tertiary
                      type="warning"
                    >
                      <n-icon size="20"> <calendar-cancel24-regular /> </n-icon>Cancel</n-button
                    >
                  </div>
                </n-space>
              </n-space>
            </n-list-item>
          </n-list>
        </n-tab-pane>
      </n-tabs>
    </n-card>
  </n-space>
</template>
<style scoped>
.n-card {
  background-color: rgb(255, 255, 255);
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  width: 600px;
  margin-top: 200px;
  margin-left: 550px;
  text-align: center;
}
.n-button {
  border-radius: 0.4rem;
  width: 20vb;
  height: 5vh;
}
.custom-Button {
  border-radius: 0.4rem;
  width: 11vb;
  height: 5vh;
}
.centered-Button {
  text-align: center;
  font-size: 14px;
}
.size-Font {
  font-size: 15px;
  font-style: italic;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
