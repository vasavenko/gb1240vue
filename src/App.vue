<template>
  <v-app>
    <!-- <v-system-bar app>SYS</v-system-bar> -->
    <v-app-bar app flat>
      <v-btn :ripple="false" plain to="/dashboard">Dashboard</v-btn>
      <v-btn :ripple="false" plain to="/about">About</v-btn>
      <v-btn :ripple="false" plain to="/404">404</v-btn>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>

import { mapActions } from 'vuex'

export default {
  name: 'App',
  data: () => ({
    //
  }),
  methods: {
    ...mapActions ([
      'fetchData'
    ]),
  },
  mounted () {
    this.fetchData()
  }
};
</script>
