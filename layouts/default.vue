<template>
  <v-app>
    <v-app-bar fixed app :color="'blue'">
      <v-toolbar-title
        class="font-weight-medium"
        :style="'color: white;'"
        v-text="title"
      />
    </v-app-bar>
    <v-main>
      <Nuxt />
    </v-main>
    <v-footer app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      title: 'VAS',
    }
  },
}
</script>
