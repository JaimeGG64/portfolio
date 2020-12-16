<template>
  <div class="main text-center flex flex-col items-center justify-center">
    <!-- <logo /> -->
    <h1 class="title">Jaime Garcia</h1>
    <h2 class="subtitle">Projects</h2>
    <dl class="project-list">
      <div class="project-item" v-for="(projectPost, index) in projectPosts" :key="index">
        <nuxt-link :to="`projects/${projectPost.slug}`">
          <img :src="projectPost.cover" />
          <dt class="project-item__title">{{ projectPost.title }}</dt>
          <dd class="project-item__desc">{{ projectPost.description }}</dd>
        </nuxt-link>
      </div>
    </dl>
  </div>
</template>

<script>
export default {
  computed: {
    projectPosts() {
      return this.$store.state.projectPosts
    },
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    }
  },
}
</script>
