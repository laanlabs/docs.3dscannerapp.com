<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="text-primary-600 ">FAQ's - Frequently Asked Questions:</h1>
      <posts post-type="faq" :amount="25" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts
    try {
      posts = await $content('faq').fetch()
    } catch (e) {
      error({ message: 'faq not found' })
    }
    return { posts }
  },
}
</script>
