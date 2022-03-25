<template>
  <v-container>
    <PhotoForm v-if="photos.length < 4" @addingPhoto="pushingPhoto" />
    <p v-else>You cannot add new photos</p>
    <v-row>
      <Photo
        v-for="photo in photos"
        :key="photo.id"
        :photo="photo"
        @openPhoto="openPhoto"
      />
    </v-row>
    <PhotoDialog :photo="currentPhoto" v-model="dialogVisible" />
  </v-container>
</template>

<script>
import Photo from '@/components/photo/Photo.vue';
import PhotoForm from '@/components/photo/PhotoForm.vue';
import PhotoDialog from '@/components/photo/PhotoDialog.vue';

export default {
  components: {
    Photo,
    PhotoForm,
    PhotoDialog,
  },
  data: () => ({
    photos: [],
    currentPhoto: {},
    dialogVisible: false,
  }),
  mounted() {
    this.fetchToDo();
  },
  methods: {
    fetchToDo() {
      this.axios
        .get('https://jsonplaceholder.typicode.com/photos?_limit=3')
        .then((response) => (this.photos = response.data));
    },
    pushingPhoto(photo) {
      this.photos.push(photo);
    },
    openPhoto(photo) {
      this.currentPhoto = photo;
      this.dialogVisible = true;
    },
  },
};
</script>

<style lang="scss" scoped></style>
