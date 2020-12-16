<template>
  <article v-if="projectPost" class="main article">
    <div class="project-header">
      <div class="project-header__text-wrapper">
        <h1 class="article-title">{{ projectPost.title }}</h1>
        <p class="mt-4">{{ projectPost.description }}</p>
      </div>
      <img class="project-header__image cover-image" :src="projectPost.cover" />
    </div>
    <div class="block mt-8 mb-4" v-html="$md.render(projectPost.body)" />
    <div v-if="projectPost.gallery">
      <img v-for="image in projectPost.gallery" class="image" :key="image.id" :src="image" />
    </div>
  </article>
</template>
<script>
export default {
  async asyncData({ params, payload }) {
    if (payload) return { projectPost: payload }
    else
      return {
        projectPost: await require(`~/assets/content/projects/${params.project}.json`),
      }
  },
}
</script>

<style lang="scss" scoped>
.project-header {
  display: grid;
  grid-template-areas: 'text image';
  grid-template-columns: 1fr 1fr;
  column-gap: 3rem;
  &__text-wrapper {
    grid-area: text;
  }
  &__image {
    grid-area: image;
  }
}
</style>
