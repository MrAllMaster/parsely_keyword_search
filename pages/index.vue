<template>
  <v-row justify="center" align="center" class="mt-12">
    <v-col cols="8">
      <search v-model="query" @search="startSearch" />
      <results :results="results" />
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      results: null,
      query: "",
    };
  },
  methods: {
    getSearchURL(query, days) {
      const parsedQuery = encodeURIComponent(query);
      const parsedDays = encodeURIComponent(days);
      return `https://api.parsely.com/v2/search?apikey=arstechnica.com&q=${parsedQuery}&days=${parsedDays}`;
    },
    async search(query, days = 30) {
      if (!query.length > 0) return;
      const searchURL = this.getSearchURL(query, days);

      try {
        this.results = await this.$axios.$get(searchURL);
      } catch (error) {
        console.log("THERE WAS AN ERROR!!!!", error);
      }
    },
    startSearch() {
      this.search(this.query);
    },
  },
  mounted() {
    this.search("apple");
  },
};
</script>
<style lang="scss">
html {
  overflow-y: auto;
}
</style>
