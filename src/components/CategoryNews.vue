<template>
  <div id="listCategory">
    <h1 class="my-5 text-center" style="color: white">Category</h1>
    <v-btn class="red mr-5 ml-3" @click="$router.back()">Kembali</v-btn>
    <v-layout row class="mx-10 text-center">
      <v-container
        v-for="category in categoryNews"
        :key="category.id"
        flex
        xs12
      >
        <v-btn class="secondary" small @click="fetchNews(category.nama)"
          >{{ category.nama }}
        </v-btn>
      </v-container>
    </v-layout>
  </div>
</template>

<script>
export default {
  computed: {
    categoryNews() {
      return this.$store.state.listCategories;
    },
  },
  methods: {
    fetchNews(value) {
      this.$store.dispatch("getCategory", value);
      this.$router.push({
        name: "genre Berita",
        params: { category: value },
      });
    },
  },
};
</script>
<style scoped>
#listCategory {
  background-color: rgb(87, 140, 255);
}
</style>
