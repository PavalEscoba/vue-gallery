<template>
  <v-col cols="4">
    <v-card @click="openPhoto">
      <v-card-title>
        {{ fullTitle }}
      </v-card-title>
      <v-card-text>
        <v-img :src="photo.url" width="200" height="200" />
      </v-card-text>
    </v-card>
  </v-col>
</template>

<script>
export default {
  props: {
    photo: {
      type: Object,
      required: true,
    },
  },
  computed: {
    fullTitle() {
      return `full Name is ${this.photo.title}`;
    },
  },
  methods: {
    openPhoto() {
      this.$emit('openPhoto', this.photo);
    },
  },
};
</script>

<style lang="scss" scoped></style>
