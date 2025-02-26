<script setup lang="ts">
const route = useRoute()
const { data: post } = await useAsyncData(route.path, () => {
  return queryCollection('blog').path(route.path).first()
})

if (!post.value) {
  throw createError({ statusCode: 404, message: 'Post not found' })
}

useSeoMeta({
  title: post.value.title,
  description: post.value.description
})
</script>

<template>
  <article>
    <ContentRenderer v-if="post" :value="post">
      <template #empty>
        <p>No content found.</p>
      </template>
    </ContentRenderer>
    
    <div class="mt-8">
      <NuxtLink to="/blog" class="text-blue-600 hover:underline">
        ← Back to all posts
      </NuxtLink>
    </div>
  </article>
</template>