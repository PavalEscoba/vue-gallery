<template>
  <v-container>
    <v-row>
      <v-col cols="6">
        <v-text-field v-model="title" />
        <v-file-input v-model="img" />
        <v-btn @click="addPhoto">Add photo</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'PhotoForm',
  data: () => ({
    title: '',
    img: null,
  }),
  methods: {
    addPhoto() {
      const reader = new FileReader();
      reader.onload = () => {
        let photo = {
          id: Date.now(),
          title: this.title,
          url: reader.result,
        };
        this.$emit('addingPhoto', photo);
      };
      reader.readAsDataURL(this.img);
    },
  },
};
</script>

<style lang="scss" scoped></style>
