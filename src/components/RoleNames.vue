<template>
  <div>
    <b-form-group v-for="(item, i) in form" :key="i" v-show="show">
      <h4>Модератор {{ ranks[i] }} ранга</h4>
      <label>Введите название в разных падежах</label>
      <b-input-group class="mt-2" v-for="(item2, i2) in item" :key="i2" :prepend="cases[i2]">
        <b-form-input
            :id="`input-role-id${i}-${i2}`"
            v-model="form[i][i2]"
        ></b-form-input>
      </b-input-group>
    </b-form-group>

    <b-button type="reset" variant="danger" v-on:click="clear">Сбросить</b-button>
  </div>
</template>

<script>
export default {
  name: "RoleNames",
  data() {
    return {
      form: {
        0: {
          nominative: '',
          genitive: '',
          instrumental: '',
          dative: '',
          plural: ''
        },
        1: {
          nominative: '',
          genitive: '',
          instrumental: '',
          dative: '',
          plural: ''
        },
        2: {
          nominative: '',
          genitive: '',
          instrumental: '',
          dative: '',
          plural: ''
        },
        3: {
          nominative: '',
          genitive: '',
          instrumental: '',
          dative: '',
          plural: ''
        },
        4: {
          nominative: '',
          genitive: '',
          instrumental: '',
          dative: '',
          plural: ''
        },
        5: {
          nominative: '',
          genitive: '',
          instrumental: '',
          dative: '',
          plural: ''
        },
      },
      ranks: {
        0: 'первого',
        1: 'второго',
        2: 'третьего',
        3: 'четвертого',
        4: 'пятого',
        5: 'шестого'
      },
      cases: {
        nominative: 'Именительный',
        genitive: 'Родительный',
        instrumental: 'Творительный',
        dative: 'Дательный',
        plural: 'Множественное число'
      },
      show: true
    }
  },
  methods: {
    clear(evt) {
      evt.preventDefault();
      for (let i = 0; i <= 5; i++) {
        this.form[i].nominative = '';
        this.form[i].genitive = '';
        this.form[i].instrumental = '';
        this.form[i].dative = '';
        this.form[i].plural = '';
      }
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    }
  },
  mounted() {
    this.$emit('mounted', this.form);
  }
}
</script>

<style scoped>

</style>