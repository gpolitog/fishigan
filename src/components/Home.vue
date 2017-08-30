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
    <h5>Fish Species Found in Michigan</h5>
    <ul>
      <li v-for="(fish, key) in fishes" :key="key">
        <p class="name">#{{key + 1}} Name: {{fish.commonname}} {{fish.latinname === undefined ? ' ' : `(${fish.latinname})`}}</p>
         <img width="400px" height="200px" :src="fetchImage(key)">
        <p>{{fish.narrative}}</p>
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
      fishes: []
    }
  },
  methods: {
    fetchImage (id) {
      if (id > 0) return require(`../assets/${id}.png`)
    },
    loadFishData () {
      this.$http.get('https://data.michigan.gov/resource/gedb-8ff3.json')
        .then(res => {
          this.fishes = res.data
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
 h5 {
   text-align: center;
 }
 li {
   list-style: none;
 }
 .name {
   font-weight: bold;
 }

</style>
