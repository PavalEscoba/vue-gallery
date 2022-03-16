<template>
  <v-container fluid>
    <v-app-bar color="orange" dark>
      <v-spacer />
      <v-btn outlined class="mr-4">
        <router-link to="/">Main page</router-link>
      </v-btn>
      <v-btn outlined>
        <router-link to="/photo">Photos</router-link>
      </v-btn>
    </v-app-bar>
  </v-container>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped></style>
