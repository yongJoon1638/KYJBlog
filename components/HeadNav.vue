<template>
  <v-app-bar app color="white" flat>
    <v-tool-bar-title class="text-no-wrap" style="margin-right: 1rem; font-weight: bold;">Dev Blog </v-tool-bar-title>
    <v-tabs color="grey darken-1" v-model="tab">
        <v-tab v-for="link in links" :key="link">
          {{ link }}
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
      links: ["Home", "About", "Category", "Updates"],
      tab: "",
    };
  },
};
</script>
