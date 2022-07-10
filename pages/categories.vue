<template>
  <div>
    <v-chip class="mr-3" v-for="(count, tagName) in contentTags" :key="index">
      <v-avatar
          left
          class="grey"
        >
          {{ count }}
        </v-avatar>{{ tagName }} 
    </v-chip>
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
  computed: {
    contentTags() {
      var tags = [];
      var tagCnt = {};

      this.articles.forEach((article) => {
        tags.push(article.tags);
      });
      tags = tags.flat();

      tags.forEach((tag) => {
        if (tagCnt[tag] !== undefined) {
          tagCnt[tag]++;
        } else {
          tagCnt[tag] = 1;
        }
      });

      return tagCnt;
    },
  },
  async asyncData({ $content, params }) {
    const articles = await $content("articles")
      .only(["title", "description", "img", "slug", "tags"])
      .sortBy("createdAt", "desc")
      .fetch();

    return {
      articles,
    };
  },
};
</script>
