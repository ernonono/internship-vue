<script setup lang="ts">
import { useHttp } from '@/composables/http/http'
import { useRouter } from 'vue-router'
const router = useRouter()
const { data } = useHttp('http://reqres.in/api/users')
</script>
<template>
  <div
    v-for="user in data?.data"
    :key="user.id"
    @click="router.push(`/dananghadi/users/${user.id}`)"
  >
    <n-card :title="user.last_name"></n-card>
  </div>
</template>
