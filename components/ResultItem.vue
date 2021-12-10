<template>
  <v-row class="mb-4">
    <v-col cols="12">
      <v-card class="elevation-0 rounded-lg pa-0" width="100%">
        <v-row no-gutters>
          <v-col cols="12" sm="4" md="3">
            <result-item-thumbnail
              :url="item.url"
              :thumbnail="item.image_url"
            />
          </v-col>
          <v-col cols="12" sm="8" md="9" class="pa-4">
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

      const formattedPublishedDate = this.$moment(publishedDate);
      const daysDifference = this.$moment().diff(
        formattedPublishedDate,
        "days"
      );
      if (daysDifference > 7) {
        return formattedPublishedDate.format("MMM D, YYYY");
      }

      return formattedPublishedDate.fromNow();
    },
  },
};
</script>
