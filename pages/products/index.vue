<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Products</h1>
      <posts post-type="products" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts
    try {
      posts = await $content('products').fetch()
    } catch (e) {
      error({ message: 'products posts not found' })
    }
    return { posts }
  },
}
</script>
