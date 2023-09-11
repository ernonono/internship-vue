<script setup lang="ts">
const todos = ref<string[]>([])

const input = ref('')
const activeTab = ref('create')

const onAddTodo = () => {
  todos.value.push(input.value)
  activeTab.value = 'list'
  input.value = ''
}
</script>

<template>
  <n-space vertical>
    <n-card title="To do List" style="margin-bottom: 16px">
      <n-tabs type="segment" animated v-model:value="activeTab">
        <n-tab-pane name="create" tab="Todo">
          <n-form @submit.prevent="onAddTodo">
            <n-form-item label="Todo">
              <n-input v-model:value="input" placeholder="Silahkan Input todo anda hari ini" />
            </n-form-item>
            <n-button attr-type="submit" type="warning">Submit</n-button>
          </n-form>
        </n-tab-pane>
        <n-tab-pane name="list" tab="List Todo">
          <n-list hoverable>
            <template v-if="todos.length === 0">
              <n-empty description="Belum ada todo">
                <template #extra>
                  <n-button type="warning"> Tambah Todo </n-button>
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
</template>
<style scoped>
.n-card {
  background-color: burlywood;
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  width: 600px;
  margin-top: 200px;
  margin-left: 450px;
}
.n-button {
  border-radius: 0.375rem;
  width: 33vw;
  height: 5vh;
}
</style>
