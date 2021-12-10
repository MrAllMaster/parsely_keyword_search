<template>
  <div>
    <p class="accent--text text-body-2 mb-1">
      <span v-for="(item, index) in breadcrumbs" :key="`${item} ${index}`">
        {{ item }}
        <span v-if="index !== breadcrumbs.length - 1">&#62;</span>
      </span>
    </p>
  </div>
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

<style lang="scss" scoped>
p {
  opacity: 0.8;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
div {
  display: grid;
}
</style>
