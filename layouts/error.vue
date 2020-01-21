<template>
  <v-app light>
    <v-content class="d-flex align-center">
      <v-container v-if="error.statusCode === 404">
        <v-row justify="center">
          <v-img src="/images/404.png" max-width="350" alt="404"/>
        </v-row>
        <v-row justify="center" class="text-center">
          <h1  style="font-size: 2.8rem; color: rgb(125, 125, 125);">PÁGINA NO ENCONTRADA</h1>
        </v-row>
        <v-row justify="center">
          <v-btn color="#008856" class="font-weight-bold" dark depressed to="/">Regresar al inicio</v-btn>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
  export default {
    layout: 'empty',
    props: {
      error: {
        type: Object,
        default: null
      }
    },
    head() {
      const title =
        this.error.statusCode === 404 ? this.pageNotFound : this.otherError
      return {
        title
      }
    },
    data() {
      return {
        pageNotFound: '404 Not Found',
        otherError: 'An error occurred'
      }
    }
  }
</script>

<style scoped>
  h1 {
    font-size: 20px;
  }
</style>
