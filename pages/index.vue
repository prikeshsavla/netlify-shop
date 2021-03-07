<template>
  <main>
    <section class="self-center flex flex-col flex-1 items-center justify-center">
      <h1 class="title text-center">Curated Amazon Accessories</h1>
      <div class="mt-12">
        Best of the products you can buy for your self and your office (home office, if you 💘 working remotely)
      </div>
      <nav class="scrim-bg z-40 top-0 inset-x-0 pt-3 px-3" aria-label="Main Menu">
        <ul class="flex">
          <li class="flex-1 ml-2">
            <nuxt-link class="btn block" to="/blog">Shop</nuxt-link>
          </li>
          <li class="flex-1 ml-2">
            <nuxt-link class="btn block" to="/projects">Projects</nuxt-link>
          </li>
        </ul>
      </nav>
    </section>

    <section class="mt-8">
      <h3 class="text-primary-600 dark:text-primary-400 max-w-5xl mx-auto">Latest blog post</h3>
      <posts post-type="blog" :amount="1" />
    </section>
  </main>
</template>