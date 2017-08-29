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
  </q-layout>
</template>

<script>
import {
  QToolbar,
  QToolbarTitle,
  QIcon,
  QLayout
} from 'quasar'
export default {
  name: 'home',
  components:{
    QToolbar,
    QToolbarTitle,
    QIcon,
    QLayout
  }
}
</script>

<style lang="stylus">

</style>
