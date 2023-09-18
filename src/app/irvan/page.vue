<route lang="yaml">
  meta:
    layout: guest
  </route>

<script setup lang="ts">

</script>

<template>
  <n-space justify="center">
  <n-card title="Login" align="center">
    <n-carousel autoplay>
    <img
      class="carousel-img"
      src="https://naive-ui.oss-cn-beijing.aliyuncs.com/carousel-img/carousel1.jpeg"
    >
    <img
      class="carousel-img"
      src="https://naive-ui.oss-cn-beijing.aliyuncs.com/carousel-img/carousel2.jpeg"
    >
    <img
      class="carousel-img"
      src="https://naive-ui.oss-cn-beijing.aliyuncs.com/carousel-img/carousel3.jpeg"
    >
    <img
      class="carousel-img"
      src="https://naive-ui.oss-cn-beijing.aliyuncs.com/carousel-img/carousel4.jpeg"
    >
  </n-carousel>
  <br>
    <n-text
              >Silahkan masukkan email & password untuk masuk ke akun anda
    </n-text>
    <br>
    <br>
    <n-form-item path="email" label="Alamat Email">
      <n-input placeholder="Email" />
    </n-form-item>
  <n-form-item path="age" label="Password">
   <n-input
      type="password"
      show-password-on="mousedown"
      placeholder="Password"
      :maxlength="8"
    />
  </n-form-item>
   <n-space item-style="display: flex;" align="center">
    <n-checkbox>Ingat Saya
    </n-checkbox>
    </n-space>
   <br>
   <n-row :gutter="[0, 24]">
     <n-col :span="14">
       <div style="display: flex; justify-content: flex-end">
         <n-button
           round
           type="primary"
         > Login
         </n-button>
       </div>
     </n-col>
   </n-row>

 </n-card>
 </n-space>
</template>

<style scoped>
.n-card {
  max-width: 450px;
  margin-top: 60px;
  position: relative;
}

.carousel-img {
  width: 100%;
  height: 240px;
  object-fit: cover;
}
</style>