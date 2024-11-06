<script setup lang="ts">
import SHButton from './components/SHButton.vue'

const onclick = () => alert('Hello!')
const target = 'https://www.google.co.jp/'
</script>

<template>
  <div class="container">
    <div class="row">
      <SHButton label="button (onclick)" theme="black" left-icon="pen" @click="onclick" />
      <SHButton label="button (target to google)" theme="black" :target="target" />
      <SHButton label="submit" theme="black" type="submit" right-icon="fish" />
      <SHButton label="disabled" theme="black" left-icon="home" right-icon="user" disabled />
      <SHButton label="loading" theme="black" loading />
      <SHButton label="width-height" theme="black" width="80%" height="100px" />
    </div>
    <div class="row">
      <SHButton label="button (onclick)" theme="white" left-icon="pen" bordered @click="onclick" />
      <SHButton label="button (target to google)" theme="white" bordered :target="target" />
      <SHButton label="submit" theme="white" bordered type="submit" right-icon="fish" />
      <SHButton
        label="disabled"
        theme="white"
        bordered
        left-icon="home"
        right-icon="user"
        disabled
      />
      <SHButton label="loading" theme="white" bordered loading />
      <SHButton label="width-height" theme="white" bordered width="80%" height="100px" />
    </div>
    <div class="row">
      <SHButton label="button (onclick)" theme="white" left-icon="pen" @click="onclick" />
      <SHButton label="button (target to google)" theme="white" :target="target" />
      <SHButton label="submit" theme="white" type="submit" right-icon="fish" />
      <SHButton label="disabled" theme="white" left-icon="home" right-icon="user" disabled />
      <SHButton label="loading" theme="white" loading />
      <SHButton label="width-height" theme="white" width="80%" height="100px" />
    </div>
  </div>
</template>

<style scoped lang="scss">
.container {
  width: 100%;
  max-width: 1600px;
  min-height: 100vh;
  margin: 0 auto;
  padding: 40px 100px;
  background-color: #f7f7f7;
  @media screen and (max-width: 767px) {
    padding: 50px 5%;
  }

  .row {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 100%;
    margin: 50px auto;
    gap: 30px;
  }
}
</style>
