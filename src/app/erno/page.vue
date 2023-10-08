<route lang="yaml">
  meta:
    layout: guest
</route>

<script setup lang="ts">

</script>

<template>
<n-space justify="center">
<n-card>
  
  <h1 class="text-2xl text-center" align="center">Login</h1>
  <n-space justify="center">
  <NIcon size="150">
    <Icons name="profile-circle-fill" />
  </NIcon>
</n-space>
    <n-form-item path="email" label="Alamat Email">
      <n-input round placeholder="Masukkan Email"/>
    </n-form-item>
  <n-form-item path="age" label="Password">
   <n-input
      type="password"
      show-password-on="click"
      round placeholder="Password"
      :maxlength="8"
    />
  </n-form-item>
  <n-space vertical>
    <n-button round quaternary >
    lupa pasword?
  </n-button>
  <n-checkbox>Ingat Saya</n-checkbox>
  </n-space>
  <br>
<n-space justify="center">
  <n-button round type="info">
    Login
  </n-button>

</n-space>
  

</n-card>
</n-space>


</template>
<style scoped>
  .n-card {
    width: 500px;
    margin-top: 200px;
  }
  .n-button{
    width: 450px;
  }
</style>
