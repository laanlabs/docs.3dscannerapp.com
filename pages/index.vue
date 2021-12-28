<template>
  <main>
    <section class="">
      <h1 class="mt-8 font-semibold text-grey-900">3D Scanner App - FAQ's, HOW-TO's and More...</h1>
      <h2 class="subtitle text-center"></h2>
    </section>

    <section class="mt-8">
      <h3 class="text-primary-600 dark:text-primary-400 max-w-5xl mx-auto">Recent FAQ's</h3>
      <posts post-type="faq" :amount="5" />
    </section>
  </main>
</template>