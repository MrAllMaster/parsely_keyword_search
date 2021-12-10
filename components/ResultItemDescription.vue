<template>
  <div class="text-body-1">
    <span>...</span>
    {{ description }}
    <a :href="url" target="blank" class="primary--text">Learn More</a>
  </div>
</template>

<script>
export default {
  props: {
    description: {
      type: String,
      required: true,
    },
    url: {
      type: String,
      required: true,
    },
  },
};
</script>
