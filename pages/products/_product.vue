<template>
  <main>
    <section v-if="post">
      <nav class="mb-8" aria-label="go back">
        <router-back class="block" />
      </nav>

      <article>
        <h5
          v-if="post.createdAt"
          class="inline-block py-1 px-2 my-2 bg-gray text-white text-sm font-medium rounded-sm whitespace-no-wrap"
        >
          {{ formatDate(post.createdAt) }}
        </h5>
        <a :href="post.link" target="_blank">
          <h1 class="">{{ post.title }}</h1></a
        >
        <p class="mt-1 mb-4 text-primary-600 dark:text-primary-400">{{ post.description }}</p>
        <p class="mt-1 mb-4" v-html="post.image"></p>
        <nuxt-content :document="post" />
      </article>
    </section>
  </main>
</template>

<script>
import * as SITE_INFO from '~/content/site/info.json'

export default {
  async asyncData({ $content, params, error }) {
    let post
    try {
      post = await $content('products', params.product).fetch()
    } catch (e) {
      error({ message: 'Products post not found' })
    }
    return { post }
  },
  head() {
    return {
      title: this.formattedTitle,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content: 'My custom description',
        },
      ],
    }
  },
  methods: {
    formatDate(dateString) {
      const date = new Date(dateString)
      return date.toLocaleDateString(process.env.lang) || ''
    },
  },
  computed: {
    formattedTitle() {
      return `${this.post.title} | ${SITE_INFO.sitename}`
    },
  },
}
</script>
