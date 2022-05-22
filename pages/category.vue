<template>
  <div>
    <v-container grid-list-xs>
      <v-row dense>
        <v-col v-for="(article, index) in articles" :key="index">
          <PostCard :post="article"></PostCard>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content("articles")
      .only(["title", "description", "img", "slug", "tags"])
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      articles,
    };
  },
};
</script>
