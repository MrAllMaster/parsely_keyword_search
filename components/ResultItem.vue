<template>
  <v-row>
    <v-card>
      <v-card-title>{{ item.title }} </v-card-title>
      <v-row>
        <v-col cols="2">
          <v-img :src="item.thumb_url_medium"></v-img>
        </v-col>
        <v-col>
          <p>
            <span>{{ item.pub_date }}</span>
            <span>...</span>
            {{ itemDescription }}
          </p>
          <p>
            Labeled <span>{{ item.section }}</span>
          </p>
        </v-col>
      </v-row>
    </v-card>
  </v-row>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  computed: {
    itemDescription(item) {
      const metadata = JSON.parse(this.item.metadata);
      return metadata.lower_deck;
    },
  },
};
</script>

<style></style>
