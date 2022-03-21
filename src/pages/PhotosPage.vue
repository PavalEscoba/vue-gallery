<template>
  <v-container>
    <PhotoForm @addPhoto="addingPhoto" />
    <v-row>
      <Photo
        v-for="photo in photos"
        :key="photo.id"
        :photo="photo"
        @openPhoto="openPhoto"
      />
    </v-row>
    <PhotoDialog :photo="currentPhoto" :v-model="dialogVisible" />
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
    value: false,
  }),
  mounted() {
    this.fetchToDo();
  },
  methods: {
    fetchToDo() {
      this.axios
        .get('https://jsonplaceholder.typicode.com/photos?_limit=10')
        .then((response) => (this.photos = response.data));
    },
    addingPhoto(photo) {
      this.photos.push(photo);
    },
    openPhoto(photo) {
      console.log(photo);
      this.currentPhoto = photo;
      this.dialogVisible = true;
    },
  },
};
</script>

<style lang="scss" scoped></style>
