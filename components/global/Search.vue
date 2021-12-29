<template>
  <div class="float-right relative">
    <div class="container flex mx-auto">
      <div class="flex border-2 rounded">
        <button class="flex items-center justify-center px-4 border-r">
          <svg class="w-6 h-6 text-gray-600" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
            <path
              d="M16.32 14.9l5.39 5.4a1 1 0 0 1-1.42 1.4l-5.38-5.38a8 8 0 1 1 1.41-1.41zM10 16a6 6 0 1 0 0-12 6 6 0 0 0 0 12z"
            ></path>
          </svg>
        </button>
        <input
          v-model="query"
          type="search"
          class="px-4 py-2 w-80 border-0"
          placeholder="Search..."
          autocomplete="off"
        />
      </div>
    </div>

    <div v-if="articles.length" class="fixed z-40 p-2 bg-white border rounded border-solid border-slate-200 shadow-md">
      <ul class="">
        <li v-for="article of articles" :key="article.slug" class="border-b-2 border-slate-200 p-2 group">
          <nuxt-link :to="`/faq/${article.slug}`" class="" @click.native="clearSearch">
            <span class="group-hover:text-indigo-500">{{ article.title }}</span>
          </nuxt-link>
          <!-- <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">{{ article.title }}</NuxtLink> -->
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'search-dropdown',
  data() {
    return {
      query: '',
      articles: [],
      open: false,
    }
  },
  watch: {
    async query(query) {
      if (!query) {
        this.articles = []
        return
      }

      this.articles = await this.$content('faq')
        .only(['title', 'slug'])
        .sortBy('createdAt', 'asc')
        .limit(12)
        .search(query)
        .fetch()
    },
  },

  methods: {
    clearSearch(e) {
      this.articles = []
      this.query = ''
    },
  },
}
</script>