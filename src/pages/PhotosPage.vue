<template>
  <v-container>
    <v-row>
      <Photo v-for="photo in photos" :key="photo.id" :photo="photo" />
    </v-row>
  </v-container>
</template>

<script>
import Photo from '@/components/photo/Photo.vue';
export default {
  components: {
    Photo,
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
        .get('https://jsonplaceholder.typicode.com/photos?_limit=10')
        .then((response) => (this.photos = response.data));
    },
  },
};
</script>

<style lang="scss" scoped></style>
