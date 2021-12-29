<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">3D Scanner App How To's</h1>
      <p>Tutorials on the most common tasks with 3D Scanner App.</p>
      <posts post-type="howtos" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts
    try {
      posts = await $content('howtos').fetch()
    } catch (e) {
      error({ message: 'howtos not found' })
    }
    return { posts }
  },
}
</script>
