<template>
  <q-layout
    ref="layout"
    view="lHh Lpr fff"
    :left-class="{'bg-grey-2': true}"
  >
    <q-toolbar slot="header" class="glossy">
      <q-btn
        flat
      >
        <q-icon name="menu" />
      </q-btn>
      <q-toolbar-title>
       Fishigan
        <div slot="subtitle">Providing comprehensive information about fishing in Michigan </div>
      </q-toolbar-title>
    </q-toolbar>
    <h5>Fish native to Michigan</h5>
    <ul>
      <li v-for="(f, key) in fish" :key="key">
        <p>Name: {{f.commonname}} {{f.latinname === undefined ? ' ' : `(${f.latinname})`}}</p>
        <p>{{f.narrative}}</p>
      </li>
    </ul>
  </q-layout>
</template>

<script>
import {QToolbar, QToolbarTitle, QIcon, QBtn, QLayout} from 'quasar'

export default {
  name: 'home',
  created () {
    this.loadFishData()
  },
  data () {
    return {
      fish: []
    }
  },
  methods: {
    loadFishData () {
      this.$http.get('https://data.michigan.gov/resource/gedb-8ff3.json')
        .then(res => {
          this.fish = res.data
          console.log(res)
        })
        .catch(err => {
          console.log(err)
        })
    }
  },
  components: {
    QToolbar,
    QToolbarTitle,
    QIcon,
    QBtn,
    QLayout
  }
}
</script>

<style lang="stylus">

</style>
