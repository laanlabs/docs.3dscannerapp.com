<template>
  <ul v-if="posts.length > 0" class="pt-4">
    <li v-for="(post, index) in posts" :key="index" class="pt-4">
      <nuxt-link :to="`${postType}/${post.slug}`" class="">
        <template v-if="postType === 'howtos'">
          <span class="flex-1">
            <h3 class="card-title">{{ post.title }}</h3>
            <p class="mt-2">{{ post.description }}</p>
          </span>
          <img v-if="post.cover" class="cover-image" :src="post.cover" />
          <!-- <span class="rounded-full">
            {{ post.category }}
          </span> -->
        </template>

        <template v-else>
          <span class="w-full">
            <span class="flex justify-between">
              <h6 class="">{{ post.title }}</h6>
              <span
                v-if="post.createdAt"
                class="
                  inline-flex
                  items-center
                  py-2
                  px-3
                  text-sm
                  font-medium
                  text-center text-white
                  bg-blue-700
                  rounded-lg
                  hover:bg-blue-800
                  focus:ring-4 focus:ring-blue-300
                  dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800
                "
              >
                <!-- {{ formatDate(post.createdAt) }} -->
                Read More...
              </span>
            </span>
            <p class="mt-2">{{ post.description }}</p>
          </span>
        </template>
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
