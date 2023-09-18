<script setup lang="ts">
import { useHttp } from '@/composables/http/http'

const { data } = useHttp('http://reqres.in/api/users')
</script>
<template>
  <div v-for="user in data?.data" :key="user.id" @click="$router.push(`/irvan/users/${user.id}`)">
    <n-card :title="user.first_name"></n-card>
  </div>
  <!-- <div>{{ data?.data }}</div> -->
</template>