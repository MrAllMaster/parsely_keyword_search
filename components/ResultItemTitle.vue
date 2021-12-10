<template>
  <div class="text-h5 font-weight-bold mb-2">
    <a :href="url" target="blank">{{ title }}</a>
  </div>
</template>

<script>
export default {
  props: {
    url: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
a {
  text-decoration: none;
}
</style>
