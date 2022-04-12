<template>
  <v-container>
    <v-img :src="oneNews.urlToImage" max-width="100%" class="rounded-lg mb-3" />
    <h2>{{ oneNews.title }}</h2>
    <h4>{{ oneNews.author }} <span></span></h4>
    <h5>
      {{ moment(oneNews.publishedAt).locale("id").format("LLLL") }}
    </h5>
    <p>{{ oneNews.content }}</p>
    <v-btn class="secondary mr-5" @click="$router.back()">Kembali</v-btn>
    <v-btn :href="oneNews.url" target="_blank" class="red darken-4 white--text"
      >Baca selengkapnya</v-btn
    >
  </v-container>
</template>
<script>
export default {
  computed: {
    oneNews() {
      return this.$store.state.oneNews;
    },
  },
  methods: {
    getNews(slug) {
      this.$store.dispatch("getNews", slug);
    },
  },
  created() {
    this.getNews(this.$route.params.slug);
  },
};
</script>
<style scoped></style>
