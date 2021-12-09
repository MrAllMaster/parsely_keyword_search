<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8">
      <search v-model="query" @search="search(query)" />
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
      return `https://api.parsely.com/v2/search?apikey=arstechnica.com&q=${encodeURIComponent(
        query
      )}&days=${encodeURIComponent(days)}`;
    },
    async search(query, days = 30) {
      const searchURL = this.getSearchURL(query, days);

      try {
        this.results = await this.$axios.$get(searchURL);
      } catch (error) {
        console.log("THERE WAS AN ERROR!!!!", error);
      }
    },
  },
};
</script>
