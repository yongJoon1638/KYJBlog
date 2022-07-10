<template>
  <div>
    <v-chip
      class="mr-3"
      :color="tagName == filter.tag ? 'pink' : 'grey'"
      text-color="white"
      label
      v-for="(count, tagName) in contentTags"
      :key="index"
      @click="filter.tag = filter.tag != tagName ? tagName : ''"
    >
      <v-icon left> mdi-label </v-icon>
      {{ tagName }}
    </v-chip>
    <v-container grid-list-xs>
      <v-row dense>
        <v-col v-for="(article, index) in filteredArticles" :key="index">
          <PostCard :post="article"></PostCard>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filter: {
        tag: "",
      },
    };
  },
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
    filteredArticles() {
      if (this.filter.tag != "") {
        return this.articles.filter((a) => a.tags.includes(this.filter.tag));
      }

      return this.articles;
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
