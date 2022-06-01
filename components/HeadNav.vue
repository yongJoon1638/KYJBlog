<template>
  <div>
    <!-- <v-app-bar color="accent-4" app max-width="1400" dense>
      <v-toolbar-title>KYJ Blog</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/category">Category</v-btn>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
      <v-btn icon href="https://github.com/yongJoon1638" target="_blank">
        <v-icon>mdi-github</v-icon>
      </v-btn>
    </v-app-bar> -->

    <v-app-bar app color="white" flat>
      <v-tabs centered color="grey darken-1" style="margin-left:48px;">
        <v-tab v-for="link in links" :key="link">
          {{ link }}
        </v-tab>
      </v-tabs>

      <v-btn
        icon
        href="https://github.com/yongJoon1638" target="_blank"
      >
        <v-icon>mdi-github</v-icon>
      </v-btn>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  data() {
    return {
      links: ["Dashboard", "Messages", "Profile", "Updates"],
    }
  },
}
</script>
