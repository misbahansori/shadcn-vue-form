<script setup lang="ts">
import { buttonVariants } from "~/components/ui/button";
</script>

<template>
  <section class="w-full py-12 md:py-24 lg:py-32 xl:py-48">
    <div class="container mx-auto px-4 md:px-6">
      <div class="flex flex-col items-center space-y-4 text-center">
        <div class="space-y-2">
          <h1
            class="text-3xl font-bold tracking-tighter sm:text-4xl md:text-5xl lg:text-6xl/none"
          >
            Welcome to Your Next Project
          </h1>
          <p
            class="mx-auto max-w-[700px] text-gray-500 md:text-xl dark:text-gray-400"
          >
            Build something amazing with Nuxt 3. Fast, modern, and ready for
            production.
          </p>
        </div>
        <div class="space-x-4">
          <NuxtLink
            :class="cn(buttonVariants({ variant: 'default' }))"
            href="#"
          >
            Get Started
          </NuxtLink>
          <NuxtLink
            :class="cn(buttonVariants({ variant: 'outline' }))"
            href="#"
          >
            Learn More
          </NuxtLink>
        </div>
      </div>
    </div>
  </section>
</template>
