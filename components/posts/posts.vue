<template>
  <ul v-if="posts.length > 0" class="pt-4">
    <li v-for="(post, index) in posts" :key="index" class="pt-4 mt-3">
      <nuxt-link :to="`/${postType}/${post.slug}`" class="">
        <span class="w-full">
          <span class="flex justify-between">
            <h6 class="text-primary-600 dark:text-primary-400">{{ post.title }}</h6>
            <span v-if="post.createdAt" class="inline-flex items-center py-2 px-3 text-sm btn-blue rounded">
              <!-- {{ formatDate(post.createdAt) }} -->
              Read More...
            </span>
            <img v-if="post.cover" class="cover-image" :src="post.cover" />
            <!-- <span class="rounded-full">
            {{ post.category }}
          </span> -->
          </span>
          <p class="mt-0">{{ post.description }}</p>
        </span>
      </nuxt-link>
    </li>
  </ul>
  <div v-else-if="loading" class="cards">
    <div v-for="placeholder in placeholderClasses" :key="placeholder.id" class="card">
      <content-placeholders :rounded="true" :class="placeholder">
        <content-placeholders-heading />
      </content-placeholders>
    </div>
  </div>
  <p v-else class="max-w-5xl mx-auto">
    {{ amount > 1 ? 'Posts not found' : 'Post not found' }}
  </p>
</template>

<script>
export default {
  name: 'FAQs',
  props: {
    postType: {
      type: String,
      default: 'faq',
      validator: (val) => ['faq', 'howtos'].includes(val),
    },
    amount: {
      // ? https://content.nuxtjs.org/fetching#limitn
      type: Number,
      default: 10,
      validator: (val) => val >= 0 && val < 100,
    },
    sortBy: {
      // ? https://content.nuxtjs.org/fetching#sortbykey-direction
      type: Object,
      default: () => ({
        key: 'slug',
        direction: 'desc', // you probably want 'asc' here
      }),
      validator: (obj) => typeof obj.key === 'string' && typeof obj.direction === 'string',
    },
  },
  data() {
    return {
      posts: [],
      loading: true,
    }
  },
  computed: {
    placeholderClasses() {
      const classes = ['w-full', 'w-2/3', 'w-5/6']
      return [...Array.from({ length: this.amount }, (v, i) => classes[i % classes.length])] // repeats classes after one another
    },
  },
  async mounted() {
    this.loading = true
    this.posts = await this.fetchPosts()
    this.loading = false
  },
  methods: {
    formatDate(dateString) {
      const date = new Date(dateString)
      return date.toLocaleDateString(process.env.lang) || ''
    },
    async fetchPosts(postType = this.postType, amount = this.amount, sortBy = this.sortBy) {
      return this.$content(postType)
        .sortBy(sortBy.key, sortBy.direction)
        .limit(amount)
        .fetch()
        .catch((err) => console.error(err) || [])
    },
  },
}
</script>
