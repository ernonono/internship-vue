<script setup lang="ts"></script>

<template>
<n-space justify="center" class="container-login">
  <n-card>
    <n-h2 class="title">Login</n-h2>
    <n-form>
      <n-input class="input-email" type="text" placeholder="email"></n-input>
      <n-input class="input-pw" type="password" placeholder="password" show-password-on="click"></n-input>
    </n-form>
    <n-space>
      <n-checkbox class="cb" size="medium" label="Remember me" />
      <n-button
        text
        tag="a"
        href="#"
        target="_blank"
        type="primary"
        class="hl">
        Forget Password?
      </n-button>
    </n-space>
    <n-button class="b-login" type="primary">
      Login
    </n-button>
  </n-card>
</n-space>
</template>
<style>

.container-login{
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
.title{
  text-align: center;
}
.b-login {
  margin-top: 10px;
  margin-left: 25%;
  width: 200px;
  
}
.n-input{
  margin-top: 10px;
}


.cb {
  margin-top: 20px;
  margin-left: 0,2cm;
  margin-right: 2cm;
  margin-bottom: 10px;
}

.hl{
  margin-top: 25px;
  margin-left: 2cm;
  margin-right: 0,2cm;
  margin-bottom: 10px;
}
</style>