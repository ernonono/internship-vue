<route lang="yaml">
    meta:
        layout: guest
    </route>
    <script setup lang="ts">

</script>

<template>
    <n-card :class="$style.container">
        <n-space justify="center" align="center" :class="$style.container">
            <div :class="$style.card_wrapper">
                <Icons name="logo" height="50" />
                <n-space justify="center">
                    <n-text> Dashboard Tele Sales eMET </n-text>
                </n-space>
            <div style="position: relative;  margin-top: 10px" >
                <n-card :class="$style.card">
                    <n-h2>Silahkan login</n-h2>
                    <n-text>
                        Masukkan email & kata sandi untuk masuk ke akun Anda
                    </n-text>
                    <div :class="$style.form">
                        <n-form>
                            <n-form-item path="email" label="Alamat Email">
                                <n-input placeholder="Email" />
                            </n-form-item>
                            <n-form-item path="password" label="Password">
                                <n-input
                                    show-password-on="click"
                                    type="password"
                                    placeholder="Password"
                                />
                            </n-form-item>
                            <n-row :gutter="[0, 24]">
                                <n-col :span="24"> 
                                    <div style="display: flex; justify-content: flex-end;">
                                        <router-link to="/counter">
                                        <n-button type="primary">
                                            Login
                                        </n-button>
                                    </router-link>
                                    </div>
                                </n-col>
                            </n-row>
                        </n-form>
                    </div>
                </n-card>
            </div>
            </div>
        </n-space>
    </n-card>
</template>

<style scoped module>
.container {
    min-height: 100vh;
}
.card {
    max-width: 500px;
}
.card_wrapper {
    display: flex;
    flex-direction: column;
    row-gap: 1rem;
  }
.form {
    margin-top: 1rem;
  }
</style>