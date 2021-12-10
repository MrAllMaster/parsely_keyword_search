<template>
  <v-row>
    <v-card>
      <v-card-title>
        <a :href="item.url" target="blank">{{ item.title }}</a>
      </v-card-title>
      <result-item-breadcrumbs :breadcrumbs="itemBreadcrumbs" />
      <v-row>
        <v-col cols="2">
          <a :href="item.url" target="blank">
            <v-img :src="item.thumb_url_medium" :href="item.url"></v-img>
          </a>
        </v-col>
        <v-col>
          <p>
            <span>{{ itemPublishedDate }}</span>
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
    itemDescription() {
      const metadata = JSON.parse(this.item.metadata);
      return metadata.lower_deck;
    },
    itemBreadcrumbs() {
      return this.item.url.split("/").slice(3, -1);
    },
    itemPublishedDate() {
      const { pub_date: publishedDate } = this.item;
      const currentMonth = this.$moment().month();
      const publishedMonth = this.$moment(publishedDate).month();

      if (currentMonth !== publishedMonth) {
        return this.$moment(publishedDate).format("MMM D, YYYY");
      }

      return this.$moment(publishedDate).fromNow();
    },
  },
};
</script>

<style></style>
