<template>
  <v-app-bar app color="white" flat>
    <v-tabs color="grey darken-1">
      <v-tab v-for="link in links" :key="link.title" :to="link.link">
        {{ link.title }}
      </v-tab>
    </v-tabs>
  </v-app-bar>
</template>

<script>
export default {
  data() {
    return {
      links: [
        {
          title: "Home",
          link: "/",
        },
        {
          title: "About",
          link: "/about",
        },
        {
          title: "Category",
          link: "/category",
        },
        {
          title: "Updates",
          link: "/updates",
        },
      ],
    };
  },
};
</script>
