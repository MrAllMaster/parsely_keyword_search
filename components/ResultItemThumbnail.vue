<template>
  <a :href="url" target="blank">
    <v-img
      class="rounded-lg"
      :class="[
        { 'rounded-b-0': $vuetify.breakpoint.xsOnly },
        { 'rounded-r-0': $vuetify.breakpoint.smAndUp },
      ]"
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
