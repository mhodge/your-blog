<template>
    <div>
      <header class="bg-gray-900 text-white p-4">
        <div class="container mx-auto">
          <h1 class="text-xl font-bold">My Nuxt Blog</h1>
          <nav class="mt-2">
            <NuxtLink to="/" class="mr-4 hover:underline">Home</NuxtLink>
            <NuxtLink to="/blog" class="hover:underline">Blog</NuxtLink>
          </nav>
        </div>
      </header>
  
      <main class="container mx-auto p-4">
        <slot />
      </main>
  
      <footer class="bg-gray-200 p-4 mt-8">
        <div class="container mx-auto text-center text-gray-700">
          © {{ new Date().getFullYear() }} My Blog
        </div>
      </footer>
    </div>
  </template>