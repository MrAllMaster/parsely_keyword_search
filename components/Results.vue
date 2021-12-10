<template>
  <v-row>
    <v-col v-if="hasResults">
      <result-item v-for="item in results.data" :key="item.url" :item="item" />
    </v-col>
    <v-col v-else>
      <no-results />
    </v-col>
  </v-row>
</template>

<script>
export default {
  props: {
    results: {
      type: Object,
      default: () => {},
    },
  },
  computed: {
    hasResults() {
      return this.results?.data.length > 0;
    },
  },
};
</script>

<style></style>
