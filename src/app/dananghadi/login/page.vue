<route lang="yaml">
meta:
  layout: guest
</route>
<script setup lang="ts"></script>

<template>
  <div :class="$style.container">
    <n-space justify="center" align="center" vertical>
      <n-h1 style="text-align: center">
        <b> ٱلسَّلَامُ عَلَيْكُمْ وَرَحْمَةُ ٱللَّٰهِ وَبَرَكَاتُهُ</b></n-h1
      >
      <n-card :class="$style.logincard">
        <n-space justify="center">
          <n-text> Dashboard Tele Sales eMET </n-text>
        </n-space>
        <n-h4>Silahkan masukkan email & kata sandi untuk masuk ke akun Anda </n-h4>
        <n-form ref="formRef">
          <n-form-item path="email" label="Email">
            <n-input round placeholder="Input Email" />
          </n-form-item>
          <n-form-item path="password" label="Password">
            <n-input round type="password" show-password-on="click" placeholder="Input Password" />
          </n-form-item>
          <n-row :gutter="[0, 30]">
            <n-col :span="24">
              <div style="display: flex; justify-content: center">
                <router-link to="/dananghadi/todo">
                  <n-button round type="success">Login</n-button></router-link
                >
              </div>
            </n-col>
          </n-row>
        </n-form>
      </n-card>
    </n-space>
  </div>
</template>
<style scoped module>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  font-family: Century Gothic;
}

.logincard {
  width: 450px;
  background-color: theme('colors.white');
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
}
</style>
