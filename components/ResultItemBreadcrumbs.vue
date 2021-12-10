<template>
  <p>
    <span v-for="(item, index) in breadcrumbs" :key="`${item} ${index}`">
      {{ item }}
      <span v-if="index !== breadcrumbs.length - 1">&#62;</span>
    </span>
  </p>
</template>

<script>
export default {
  props: {
    breadcrumbs: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style></style>
