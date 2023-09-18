<script setup lang="ts">
import { useHttp } from '@/composables/http/http'

const { data } = useHttp('http://reqres.in/api/users')
</script>
<template>
  <div>{{ data }}</div>
</template>
