<template>
  <div class="page-wrap">
    <div class="content">
      <h1 class="app-name">今日のおしごと</h1>
      <div class="btn btn--white">
        <img class="btn__logo" src="../assets/google-logo.png" alt="" />
        <p class="btn__text">Googleアカウントでログイン</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView",
};
</script>

<style lang="scss" scoped>
.app-name {
  color: #ffffff;
  font-size: 32px;
  font-family: Kaisei Opti;
  text-align: center;
  margin-bottom: 48px;
}

.page-wrap {
  height: calc(100vh - 56px);
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
}

.btn {
  background-color: #ffffff;
  border-radius: 50px;
  border: none;
  height: 32px;
  width: 240px;
  display: flex;
  align-items: center;
  justify-content: center;

  &__logo {
    width: 16px;
    height: 16px;
    margin-right: 8px;
  }

  &__text {
    color: #404040;
    font-size: 14px;
    font-family: Kaisei Opti;
    font-weight: bold;
    padding-top: 2px;
  }
}
</style>
