<template>
  <v-row class="mb-4">
    <v-col cols="12">
      <v-card class="elevation-0 rounded-lg pa-0" width="100%">
        <v-row no-gutters>
          <v-col cols="3">
            <result-item-thumbnail
              :url="item.url"
              :thumbnail="item.thumb_url_medium"
            />
          </v-col>
          <v-col class="pa-4">
            <result-item-title :url="item.url" :title="item.title" />
            <result-item-breadcrumbs :breadcrumbs="breadcrumbs" />
            <result-item-information
              :publishedDate="publishedDate"
              :section="item.section"
            />
            <result-item-description
              :description="description"
              :url="item.url"
            />
          </v-col>
        </v-row>
      </v-card>
    </v-col>
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
    description() {
      const metadata = JSON.parse(this.item.metadata);
      return metadata.lower_deck;
    },
    breadcrumbs() {
      const breadcrumbs = this.item.url.split("/").slice(3, -1);
      breadcrumbs.unshift("Ars Technica");
      return breadcrumbs;
    },
    publishedDate() {
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
