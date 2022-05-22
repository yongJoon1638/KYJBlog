<template>
  <v-card :loading="loading" class="mx-auto my-12" max-width="374">
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      height="250"
      src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
    ></v-img>

    <v-card-title>{{ post.title }}</v-card-title>

    <v-card-text>
      <div>{{ post.description }}</div>
    </v-card-text>
    <v-card-text>
      <v-chip-group
        active-class="deep-purple accent-4 white--text"
        column
      >
        <v-chip v-for="(tag, index) in resolvedTags" :key="index">{{ tag }}</v-chip>
      </v-chip-group>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  computed: {
    resolvedTags() {
      if (!this.post.tags || Array.isArray(this.post.tags)) return this.post.tags
      return [this.post.tags];
    }
  }
}
</script>
