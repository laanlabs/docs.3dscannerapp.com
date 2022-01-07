<template>
  <nav class="container mx-auto p-2" aria-label="Main Menu">
    <ul class="flex">
      <li class="flex-none">
        <nuxt-link class="btn btn-blue" to="/">Home</nuxt-link>
      </li>
      <li class="flex-none ml-2">
        <nuxt-link class="btn btn-blue" to="/faq">FAQs</nuxt-link>
      </li>
      <li class="flex-none ml-2">
        <nuxt-link class="btn btn-blue" to="/howtos">How-Tos</nuxt-link>
      </li>
      <li class="flex-grow ml-2">
        <Search />
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Header',
}
</script>

