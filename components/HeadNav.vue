<template>
  <v-app-bar app color="white" flat>
    <v-tool-bar-title
      class="text-no-wrap"
      style="margin-right: 1rem; font-weight: bold"
      >Yong Joon`s Dev Blog
    </v-tool-bar-title>
    <v-tabs color="grey darken-1">
      <v-tab v-for="link in links" :key="link.title" :to="link.link">
        {{ link.title }}
      </v-tab>
    </v-tabs>
    <v-spacer></v-spacer>
    <v-responsive max-width="260">
      <v-text-field
        dense
        flat
        hide-details
        rounded
        solo-inverted
      ></v-text-field>
    </v-responsive>
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
