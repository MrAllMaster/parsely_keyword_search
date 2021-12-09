<template>
  <v-row>
    <v-text-field
      label="Search"
      :value="value"
      @input="$emit('update', $event)"
      v-on:keyup.enter="search"
      placeholder="Search in Ars Technica"
    >
    </v-text-field>
    <v-btn elevation="2" @click="search">Search</v-btn>
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

<style></style>
