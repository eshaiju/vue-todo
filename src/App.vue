<template>
  <v-app>
    <Header />
    <v-progress-linear :indeterminate="true" v-if="loaderStatus"></v-progress-linear>
    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>
import { mapGetters } from "vuex";

import Header from './components/layout/Header'

export default {
  name: 'Add',
  computed: mapGetters(['loaderStatus']),
  components: {
    Header
  }
}
</script>

<style>
</style>
