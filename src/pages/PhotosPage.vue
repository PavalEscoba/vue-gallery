<template>
  <v-container>
    <PhotoForm @addingPhoto="pushingPhoto" />
    <v-row>
      <Photo v-for="photo in photos" :key="photo.id" :photo="photo" />
    </v-row>
  </v-container>
</template>

<script>
import Photo from '@/components/photo/Photo.vue';
import PhotoForm from '@/components/photo/PhotoForm.vue';

export default {
  components: {
    Photo,
    PhotoForm,
  },
  data: () => ({
    photos: [],
  }),
  mounted() {
    this.fetchToDo();
  },
  methods: {
    fetchToDo() {
      this.axios
        .get('https://jsonplaceholder.typicode.com/photos?_limit=2')
        .then((response) => (this.photos = response.data));
    },
    pushingPhoto(photo) {
      this.photos.push(photo);
    },
  },
};
</script>

<style lang="scss" scoped></style>
