<template>
  <div>
    <b-form-group v-show="show">
      <h4>Должности</h4>
      <label>Введите название в разных падежах</label>
      <b-input-group class="mt-2" v-for="(item, i) in form" :key="i" :prepend="cases[i]">
        <b-form-input
            :id="'input-position-' + i"
            v-model="form[i]"
        ></b-form-input>
      </b-input-group>
    </b-form-group>

    <b-button type="reset" variant="danger" v-on:click="clear">Сбросить</b-button>
  </div>
</template>
<script>
export default {
  name: "PositionNames",
  data() {
    return {
      form: {
        nominative: '',
        genitive: '',
        instrumental: '',
        dative: '',
        plural: ''
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
      this.form.nominative = '';
      this.form.genitive = '';
      this.form.instrumental = '';
      this.form.dative = '';
      this.form.plural = '';
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