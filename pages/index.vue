<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-row>
        <v-text-field
          label="Search"
          placeholder="Search in Ars Technica"
        ></v-text-field>
        <v-btn elevation="2">Search</v-btn>
      </v-row>
      <div v-if="results">
        <result-item
          v-for="item in results.data"
          :key="item.url"
          :item="item"
        />
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      results: null,
    };
  },
  methods: {
    getSearchURL(query, days) {
      return `https://api.parsely.com/v2/search?apikey=arstechnica.com&q=${encodeURIComponent(
        query
      )}&days=${encodeURIComponent(days)}`;
    },
    async search(query, days, resultsCallback) {
      const searchURL = this.getSearchURL(query, days);

      try {
        this.results = await this.$axios.$get(searchURL);
      } catch (error) {
        console.log("THERE WAS AN ERROR!!!!", error);
      }
    },
  },
  mounted() {
    this.search("microsoft@?", 30);
  },
};
</script>
