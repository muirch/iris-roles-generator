<template>
  <div id="app">
    <div>
      <b-navbar variant="faded" type="light" class="text-center">
        <b-navbar-brand tag="h1" class="m-auto">Помощник-генератор ролей {{ version }}</b-navbar-brand>
      </b-navbar>
    </div>
    <router-view/>
  </div>
</template>

<script>
import { version } from '../package.json';

export default {
  name: 'App',
  data() {
    return {
      version
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.input-group {
  .input-group-prepend {
    flex: 0 0 25%;
  }
  .input-group-text {
    width: 100%;
  }
}

#nav {
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
