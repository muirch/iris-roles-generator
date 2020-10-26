<template>
  <div>
    <b-container class="generator__container p-2">
      <div>
        <b-tabs content-class="mt-3">
          <b-tab title="Ранги модераторов" active>
            <RoleNames v-on:mounted="gatherData" />
          </b-tab>
          <b-tab title="Названия рангов">
            <RanksNames v-on:mounted="gatherData" />
          </b-tab>
          <b-tab title="Названия должностей">
            <PositionNames v-on:mounted="gatherData" />
          </b-tab>
          <b-tab title="Результат">
            <b-card class="mt-3" header="Результат">
              <pre class="m-0 to_copy">{{ commandString }}</pre>
            </b-card>
            <b-button class="mt-2 mb-2" type="copy" variant="success" v-on:click="copyToClipboard">Скопировать</b-button>
            <p v-show="copied">Скопировано!</p>
          </b-tab>
        </b-tabs>
      </div>
    </b-container>
  </div>
</template>

<script>
import RoleNames from "../components/RoleNames";
import RanksNames from "../components/RanksNames";
import PositionNames from "../components/PositionNames";

export default {
  components: {
    RoleNames,
    RanksNames,
    PositionNames
  },
  data() {
    return {
      finalData: [],
      copied: false
    }
  },
  computed: {
    commandString() {
      let str = '';
      if (this.finalData.length > 0) {
        const roles = this.finalData[0];
        const ranks = this.finalData[1];
        const positions = this.finalData[2];
        str = `модераторы названия
0 и=${roles[0]['nominative']};р=${roles[0]['genitive']};д=${roles[0]['instrumental']};т=${roles[0]['dative']};мн=${roles[0]['plural']}
1 и=${roles[1]['nominative']};р=${roles[1]['genitive']};д=${roles[1]['instrumental']};т=${roles[1]['dative']};мн=${roles[1]['plural']}
2 и=${roles[2]['nominative']};р=${roles[2]['genitive']};д=${roles[2]['instrumental']};т=${roles[2]['dative']};мн=${roles[2]['plural']}
3 и=${roles[3]['nominative']};р=${roles[3]['genitive']};д=${roles[3]['instrumental']};т=${roles[3]['dative']};мн=${roles[3]['plural']}
4 и=${roles[4]['nominative']};р=${roles[4]['genitive']};д=${roles[4]['instrumental']};т=${roles[4]['dative']};мн=${roles[4]['plural']}
5 и=${roles[5]['nominative']};р=${roles[5]['genitive']};д=${roles[5]['instrumental']};т=${roles[5]['dative']};мн=${roles[5]['plural']}

ранг и=${ranks['nominative']};р=${ranks['genitive']};д=${ranks['instrumental']};т=${ranks['dative']};мн=${ranks['plural']}
должность и=${positions['nominative']};р=${positions['genitive']};д=${positions['instrumental']};т=${positions['dative']};мн=${positions['plural']}`;
      }
      return str;
    }
  },
  methods: {
    gatherData(data) {
      this.finalData.push(data);
    },
    copyToClipboard() {
      let text = this.commandString;
      let dummy = document.createElement("textarea");
      document.body.appendChild(dummy);
      dummy.value = text;
      dummy.select();
      const status = document.execCommand("copy");
      document.body.removeChild(dummy);
      if (status) {
        this.copied = true;
        setTimeout(() => {
          this.copied = false;
        }, 2000)
      }
    }
  },
}
</script>

<style lang="scss" scoped>
.generator__container {
  max-width: 800px;
}
.input-group {
  .input-group-prepend {
    flex: 0 0 25%;
  }
  .input-group-text {
    width: 100%;
  }
}
</style>