<template>
  <div v-if="hasResults">
    <result-item v-for="item in results.data" :key="item.url" :item="item" />
  </div>
  <no-results v-else />
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
