<template>
  <div class="header">
    <fa class="fa-bars" :icon="['fas', 'bars']" @click="toggleSideNav" />
    <fa class="fa-sign-out" :icon="['fas', 'arrow-right-from-bracket']" />
  </div>

  <SideNav v-if="$store.state.sideNav" />
  <!-- storeのstate内のsideNavの状態を取得(Vuex) -->
  <main>
    <router-view />
  </main>
</template>
<script>
import "normalize.css";
// コンポーネンツからSideNavをインポート
import SideNav from "./components/SideNav.vue";
// storeのactionを参照するためにmapActions関数をimport
import { mapActions } from "vuex";
export default {
  name: "App",
  components: {
    // インポートしたSidenavをコンポートネントとして定義
    SideNav,
  },
  methods: {
    // mapActionsでstore内のacctionsのtoggleSideNavを呼び出してくる
    ...mapActions(["toggleSideNav"]),
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  // color: #2c3e50;
}

* {
  box-sizing: border-box;
}

h1,
h2,
p {
  margin: 0;
}

body {
  background-color: #4193a1;
}

.header {
  background-color: #f6e603;
  height: 56px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 20px;
  box-shadow: 0px 3px 6px rgba($color: #000000, $alpha: 0.16);
}

.fa-bars,
.fa-sign-out {
  color: #ffffff;
  font-style: 20px;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
