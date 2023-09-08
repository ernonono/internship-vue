<route lang="yaml">
meta:
  layout: guest
</route>
<script setup lang="ts"></script>

<template>
  <div :class="$style.container">
    <n-space justify="center" align="center" vertical>
      <n-h1 style="text-align: center; font-family: Century Gothic">
        <b> ٱلسَّلَامُ عَلَيْكُمْ وَرَحْمَةُ ٱللَّٰهِ وَبَرَكَاتُهُ</b></n-h1
      >
      <n-card :class="$style.logincard">
        <Icons name="logo" height="50" />
        <n-space justify="center">
          <n-text :style="{ fontFamily: 'Century Gothic' }"> Dashboard Tele Sales eMET </n-text>
        </n-space>
        <n-h4 :style="{ fontFamily: 'Century Gothic' }"
          >Silahkan masukkan email & kata sandi untuk masuk ke akun Anda
        </n-h4>
        <n-form ref="formRef">
          <n-form-item path="email" label="Email" :style="{ fontFamily: 'Century Gothic' }">
            <n-input round placeholder="Input Email" />
          </n-form-item>
          <n-form-item path="password" label="Password" :style="{ fontFamily: 'Century Gothic' }">
            <n-input round type="password" show-password-on="click" placeholder="Input Password" />
          </n-form-item>
          <n-row :gutter="[0, 30]">
            <n-col :span="24">
              <div style="font-family: Century Gothic; display: flex; justify-content: center">
                <router-link to="/logintry/count">
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
.n-card {
  background-color: theme('colors.white');
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  width: 450px;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.logincard {
  width: 450px;
}
</style>
