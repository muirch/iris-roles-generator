<template>
  <div id="app">
    <div>
      <b-navbar variant="faded" type="light" class="text-center">
        <b-navbar-brand tag="h1" class="m-auto">Помощник-генератор ролей {{ version }}</b-navbar-brand>
      </b-navbar>
      <b-container class="description">
        <label>Данный инструмент предоставляет удобный интерфейс для редактирования ролей беседы с ботом <a href="https://vk.com/iris_cm" target="_blank">Iris</a>. Для того, чтобы ознакомиться с инструкцией, <a href="#" v-b-modal.modal-center>нажмите сюда</a>.</label>
        <b-modal id="modal-center" centered title="Инструкция">
          <p>Все довольно просто:</p>
          <ul>
            <li>Заполните все поля</li>
            <li>Перейдите на вкладку результат и нажмите кнопку скопировать</li>
            <li>Вернитесь в беседу с ботом Iris и отправьте скопированную команду</li>
          </ul>
          <template #modal-footer>
              <b-button variant="primary" size="md" class="w-25 float-right" block @click="$bvModal.hide('modal-center')">Понятно</b-button>
          </template>
        </b-modal>
      </b-container>
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

.description {
  max-width: 800px !important;
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
