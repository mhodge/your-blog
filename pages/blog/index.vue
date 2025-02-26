<script setup lang="ts">
const { data: posts } = await useAsyncData('blog', () => queryCollection('blog').all())
  
useSeoMeta({
  title: 'Blog',
  description: 'All blog posts'
})
</script>

<template>
  <div>
    <h1 class="text-3xl font-bold mb-6">Blog Posts</h1>
    
    <div v-if="posts && posts.length">
      <div v-for="post in posts" :key="post.path" class="mb-6 p-4 border border-gray-200 rounded-lg">
        <h2 class="text-xl font-semibold">
          <NuxtLink :to="post.path" class="text-blue-600 hover:underline">
            {{ post.title }}
          </NuxtLink>
        </h2>
        <div class="text-gray-500 text-sm mt-1" v-if="post.date">
          {{ new Date(post.date).toLocaleDateString() }}
        </div>
        <p class="mt-2">{{ post.description }}</p>
        <NuxtLink :to="post.path" class="text-blue-600 hover:underline mt-2 inline-block">
          Read more
        </NuxtLink>
      </div>
    </div>
    <p v-else>No blog posts found.</p>
  </div>
</template>