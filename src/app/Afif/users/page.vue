<script setup lang="ts">
import { useHttp } from '@/composables/http/http'

const router = useRouter()
const { data } = useHttp('https://reqres.in/api/users')
</script>
<template>
  <div v-for="user in data?.data" :key="user.id" @click="router.push(`/afif/users/${user.id}`)">
    <n-card :title="user.first_name"></n-card>
  </div>
  <!-- <div>{{ data?.data }}</div> -->
</template>
<style scoped>
.n-card {
  background-color: theme('colors.white');
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  width: 500px;
  margin-top: 10px;
  margin-left: 35vw;
  text-align: center;
}
</style>
