<template>
  <div class="side-nav">
    <div class="user">
      <img src="../assets/IMG_2858.jpg" alt="" class="user__img" />
      <p class="user__name">ユーザー</p>
    </div>
    <nav>
      <!-- サーバーへのリクエストを行わずにページを返す（SPA） -->
      <router-link to="/" class="side-nav__link" @click="toggleSideNav">ホーム</router-link>
      <router-link to="/form" class="side-nav__link" @click="toggleSideNav">入力しましょう</router-link>
      <router-link to="/list" class="side-nav__link" @click="toggleSideNav">することリスト</router-link>
    </nav>
  </div>

  <div class="overlay" @click="toggleSideNav"></div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "SideNav",
  methods: {
    ...mapActions(["toggleSideNav"]),
  },
};
</script>

<style lang="scss" scoped>
.side-nav {
  background-color: #ffffff;
  height: 100vh;
  width: 50vw;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 2;

  nav {
    display: flex;
    flex-flow: column;
    row-gap: 28px;
    padding-top: 28px;
    padding-left: 28px;
  }

  &__link {
    color: #221233;
    column-gap: 28px;
    font-size: 14px;
    font-family: Kaisei Opti;
    text-decoration: none;
  }
}

.user {
  height: 56px;
  padding-left: 20px;
  border-bottom: 1px solid rgba($color: #404040, $alpha: 0.5);
  display: flex;
  align-items: center;

  &__img {
    height: 40px;
    width: 40px;
    border-radius: 50%;
    margin-right: 10px;
  }

  &__name {
    color: #221233;
    font-size: 14px;
    font-family: Kaisei Opti;
  }
}

.overlay {
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
  background-color: rgba($color: #213312, $alpha: 0.5);
  z-index: 1;
}
</style>
