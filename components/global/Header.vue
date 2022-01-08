<template>
  <nav class="bg-gray-200 relative flex flex-wrap items-center justify-between px-2 py-3 mb-3">
    <div class="container px-4 mx-auto flex flex-wrap items-center justify-between max-w-screen-lg">
      <div class="w-full relative flex justify-between lg:w-auto px-4 lg:static lg:block lg:justify-start">
        <a
          class="text-sm font-bold leading-relaxed inline-block mr-4 py-2 whitespace-nowrap uppercase text-black"
          href="/"
        >
          3D Scanner App
        </a>
        <button
          class="
            text-black
            cursor-pointer
            text-xl
            leading-none
            px-3
            py-1
            border border-solid border-transparent
            rounded
            bg-transparent
            block
            lg:hidden
            outline-none
            focus:outline-none
          "
          type="button"
          v-on:click="toggleNavbar()"
        >
          <font-awesome-icon :icon="['fas', 'bars']" />
        </button>
      </div>
      <div v-bind:class="{ hidden: !showMenu, flex: showMenu }" class="lg:flex lg:flex-grow items-center">
        <ul class="flex flex-col lg:flex-row list-none ml-auto">
          <li v-for="(item, index) in items" :key="index" class="nav-item">
            <a
              :href="item.href"
              class="px-3 py-2 flex items-center uppercase font-bold leading-snug hover:opacity-75 text-black"
            >
              {{ item.title }}
            </a>
          </li>
          <li class="nav-item">
            <Search />
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      showMenu: false,
      items: [
        {
          title: 'Home',
          href: '/',
        },
        {
          title: 'FAQs',
          href: '/faq',
        },
        {
          title: 'How-Tos',
          href: '/howtos',
        },
      ],
    }
  },
  methods: {
    toggleNavbar: function () {
      this.showMenu = !this.showMenu
    },
  },
}
</script>

