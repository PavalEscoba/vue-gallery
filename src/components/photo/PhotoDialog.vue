<template>
  <v-dialog v-model="value" max-width="600">
    <v-card>
      <v-card-title>{{ photo.title }} </v-card-title>
      <v-card-text>
        <v-img :src="photo.url" />
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  propd: {
    photo: {
      type: Object,
      required: true,
    },
  },
  data: () => ({
    dialogVisible: false,
  }),
  created() {
    this.dialogVisible = this.value;
  },
  watch: {
    value(newValue) {
      this.dialogVisible = newValue;
    },
  },
};
</script>

<style lang="scss" scoped></style>
