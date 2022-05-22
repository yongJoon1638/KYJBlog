<template>
  <div>
    <v-app-bar color="black accent-4" app max-width="1400" dense>
      <v-toolbar-title>KYJ Blog</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/category">Category</v-btn>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
      <v-btn icon href="https://github.com/yongJoon1638" target="_blank">
        <v-icon>mdi-github</v-icon>
      </v-btn>
    </v-app-bar>
  </div>
</template>

<style>
.v-toolbar {
  margin: auto;
}
</style>
