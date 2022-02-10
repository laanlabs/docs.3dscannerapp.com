<template>
  <main>
    <section v-if="post">
      <nav class="mb-8" aria-label="go back">
        <router-back class="block" />
      </nav>

      <article>
        <h1 class="text-primary-600 dark:text-primary-400">{{ post.title }}</h1>
        <p class="mt-1 mb-4 text-primary-600 dark:text-primary-400">{{ post.description }}</p>
        
        <nuxt-content :document="post" />

        <span class="italic text-sm text-slate-400">Updated: {{ formatDate(post.createdAt) }}</span>
      </article>
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let post
    try {
      post = await $content('faq', params.faq).fetch()
    } catch (e) {
      error({ message: 'faq post not found' })
    }
    return { post }
  },
  methods: {
    formatDate(dateString) {
      const date = new Date(dateString)
      return date.toLocaleDateString(process.env.lang) || ''
    },
  },
}
</script>
