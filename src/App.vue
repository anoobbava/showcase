<template>
  <v-app>
    <!-- display nav bar -->
    <nav-bar></nav-bar>
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
