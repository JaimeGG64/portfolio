<template>
  <main v-if="projectPosts" class="main">
    <h1 class="title text-left">Projects</h1>
    <dl class="project-list">
      <div class="project-item" v-for="(projectPost, index) in projectPosts" :key="index">
        <nuxt-link :to="`projects/${projectPost.slug}`">
          <img :src="projectPost.cover" />
          <dt class="project-item__title">{{ projectPost.title }}</dt>
          <dd class="project-item__desc">{{ projectPost.description }}</dd>
        </nuxt-link>
      </div>
    </dl>
  </main>
</template>
<script>
export default {
  computed: {
    projectPosts() {
      return this.$store.state.projectPosts
    },
  },
}
</script>

<style lang="scss">
.project-list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  column-gap: 1rem;
}
.project-item {
  background: white;
  &__title {
    font-weight: bold;
    font-size: 1.75rem;
  }
  &__desc {
    font-weight: 400;
  }
  &__title,
  &__desc {
    text-align: left;
    padding: 0.5rem 1.5rem;
  }
}
</style>