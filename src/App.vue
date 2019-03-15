<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-light">{{title}}</span>
      </v-toolbar-title>
    </v-toolbar>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      title: process.env.VUE_APP_TITLE
    }
  }
}
</script>
