<template>
  <nav class="fixed z-40 top-0 pt-3 px-3" aria-label="Main Menu">
    <ul class="flex">
      <li class="flex-2">
        <nuxt-link class="btn btn-blue" to="/">Home</nuxt-link>
      </li>
      <li class="flex-2 ml-2">
        <nuxt-link class="btn btn-blue" to="/faq">FAQs</nuxt-link>
      </li>
      <li class="flex-2 ml-2">
        <nuxt-link class="btn btn-blue" to="/howtos">How-Tos</nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style lang="postcss" scoped>
.btn {
  @apply font-bold py-2 px-4 rounded block border-none;
}
.btn-blue {
  @apply bg-blue-500 text-white;
}
.btn-blue:hover {
  @apply bg-blue-700;
}

.nuxt-link-exact-active {
  @apply text-gray-200 border-gray-400 bg-gray-800 bg-opacity-25 cursor-default;
}

.light {
  & .scrim-bg {
    &::after {
      animation-name: fadeIn2;
      background: linear-gradient(to bottom, #e5e7eb, cubic-bezier(0.15, 0, 0.45, 1), transparent);
    }
  }
  & .nuxt-link-exact-active {
    @apply text-primary-700 border-gray-600 bg-gray-100;
  }
}

/* Need two because of smoother switching between color modes */
@keyframes fadeIn1 {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@keyframes fadeIn2 {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
