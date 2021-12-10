<template>
  <a :href="url" target="blank">
    <v-img
      class="rounded-lg rounded-r-0"
      :src="thumbnail"
      max-height="100%"
      height="100%"
    ></v-img>
  </a>
</template>

<script>
export default {
  props: {
    url: {
      type: String,
      required: true,
    },
    thumbnail: {
      type: String,
      required: true,
    },
  },
};
</script>
