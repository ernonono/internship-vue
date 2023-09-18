<script setup lang="ts">
import { useHttp } from '@/composables/http/http'
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

const { data } = useHttp(computed(() => `http://reqres.in/api/users/${route.params.id}`))
</script>
<template>
  <n-card :title="`${data?.data.first_name} ${data?.data.last_name}`" justify="center">
    <p>{{ data?.data.email }}</p>
    <n-image :src="data?.data.avatar"></n-image
  ></n-card>
</template>
<style scoped>
.n-card {
  background-color: theme('colors.white');
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  width: 500px;
  margin-top: 20px;
}
</style>