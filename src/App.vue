<template>
  <v-app>
    <!-- display nav bar -->
    <nav-bar></nav-bar>
    <!-- display router view -->
    <router-view></router-view>
  </v-app>
</template>

<script>
import NavBar from '@/views/NavBar'

export default {
  name: 'App',
  components: {
    NavBar
  }
}
</script>
