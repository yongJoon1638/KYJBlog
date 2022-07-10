<style>
.nuxt-content h2 {
  font-weight: bold;
  font-size: 28px;
}
.nuxt-content h3 {
  font-weight: bold;
  font-size: 22px;
}
.nuxt-content p {
  margin-bottom: 20px;
}
</style>

<template>
  <article>
    <div>
      {{ formatDate(article.updatedAt) }}
    </div>
    <div>
      <h1>{{ article.title }}</h1>
      <small>{{ article.description }}</small>
    </div>
    <img :src="article.img" :alt="article.alt" />
    <nuxt-content :document="article" />
    
    <v-navigation-drawer absolute permanent right>
      <v-list v-for="link in article.toc" :key="link.id">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>{{ link.text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content("articles", params.slug).fetch();

    return { article };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
};
</script>
