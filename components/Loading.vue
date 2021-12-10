<template>
  <div class="loader-wrapper">
    <div class="loader-container">
      <v-progress-circular
        v-if="loading"
        indeterminate
        size="85"
        color="primary"
      ></v-progress-circular>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    loading: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped>
.loader-wrapper {
  position: relative;
  height: 100%;
  width: 100%;
}
.loader-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  margin-top: 48px;
}
</style>
