<template>
  <v-row class="mb-12 px-3">
    <v-text-field
      label="Search"
      solo
      hide-details
      flat
      class=".rounded-pill"
      :value="value"
      @input="$emit('update', $event)"
      v-on:keyup.enter="search"
      placeholder="Search in Ars Technica"
    >
      <template #prepend-inner>
        <v-icon class="ml-1">mdi-magnify</v-icon>
      </template>
    </v-text-field>

    <v-btn
      color="primary"
      x-large
      elevation="0"
      max-height="auto"
      class="rounded-lg rounded-l-0"
      @click="search"
      >Search</v-btn
    >
  </v-row>
</template>

<script>
export default {
  model: {
    prop: "value",
    event: "update",
  },
  props: {
    value: {
      type: [String, Number],
      default: "",
    },
  },
  methods: {
    search() {
      this.$emit("search");
    },
  },
};
</script>

<style lang="scss" scoped>
.v-btn {
  height: auto !important;
  text-transform: none !important;
}
.v-text-field {
  border-radius: 8px 0 0 8px !important;
}
</style>
