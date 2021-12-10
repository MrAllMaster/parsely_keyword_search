<template>
  <div class="mb-7">
    <span class="mr-4 text-body-2">
      <v-icon color="secondary">mdi-timer-outline</v-icon>
      {{ publishedDate }}
    </span>
    <span class="text-body-2">
      <v-icon color="secondary ">mdi-label-outline</v-icon>
      {{ section }}
    </span>
  </div>
</template>

<script>
export default {
  props: {
    publishedDate: {
      type: String,
      required: true,
    },
    section: {
      type: String,
      required: true,
    },
  },
};
</script>

<style></style>
