<template>
  <nav>
    <router-link to="/">
      <div class="navigation__logo">
        Twotter
      </div>
    </router-link>
    <div class="navigation__user" v-if="user">
      {{ user.username }}
    </div>
  </nav>
  <router-view />
  <router-view />
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 5%;
    width:90%;
    background-color: deeppink;
    color: white;

    .navigation__logo {
      font-weight: bold;
      font-size: 24px;
    }

    .navigation__user {
      font-weight: bold;
    }
  }
}
</style>
