<template>
  <v-app id="sandbox">
    <v-app-bar :clipped-left="primaryDrawer.clipped" app>
      <v-btn text nuxt href="/">
      ShopsHours
      </v-btn>
      <v-spacer />

      <v-btn icon nuxt href="/shops">
        <v-icon>mdi-store</v-icon>
      </v-btn>
    </v-app-bar>
    <nuxt/>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      drawers: ['Default (no property)', 'Permanent', 'Temporary'],
      primaryDrawer: {
        model: null
      },
    }),
  }
</script>
