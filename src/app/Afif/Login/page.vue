<route lang="yaml">
meta:
  layout: guest
</route>
<script setup lang="ts"></script>
<template>
  <n-space justify="center">
    <n-card>
      <n-carousel autoplay>
        <img
          class="carousel-img"
          src="https://naive-ui.oss-cn-beijing.aliyuncs.com/carousel-img/carousel1.jpeg"
        />
        <img
          class="carousel-img"
          src="https://naive-ui.oss-cn-beijing.aliyuncs.com/carousel-img/carousel2.jpeg"
        />
        <img
          class="carousel-img"
          src="https://naive-ui.oss-cn-beijing.aliyuncs.com/carousel-img/carousel3.jpeg"
        />
        <img
          class="carousel-img"
          src="https://naive-ui.oss-cn-beijing.aliyuncs.com/carousel-img/carousel4.jpeg"
        />
      </n-carousel>
      <n-space justify="center">
        <h1 class="text-2xl text-center">LOGIN</h1>
        <n-gradient-text gradient="linear-gradient(90deg, red 0%, green 50%, blue 100%)">
          <h1 class="text-2xl text-center">Sekarang</h1>
        </n-gradient-text>
      </n-space>

      <n-form>
        <n-form-item path="email" label="Email">
          <n-input round placeholder="Masukan Email Anda" />
        </n-form-item>
        <n-form-item path="password" label="Password">
          <n-input
            round
            placeholder="Masukan Password"
            type="password"
            show-password-on="mousedown"
          />
        </n-form-item>
        <n-space justify="center">
          <router-link to="/test"><n-button type="primary">LOGIN</n-button></router-link>
        </n-space>
      </n-form>
    </n-card>
  </n-space>
</template>
<style scoped>
.n-card {
  background-color: theme('colors.white');
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  width: 600px;
  margin-top: 50px;
}
.carousel-img {
  width: 100%;
  height: 240px;
  object-fit: cover;
}
.n-button {
  border-radius: 0.375rem;
  width: 10vw;
  height: 5vh;
}
</style>
