<script setup lang="ts">
import { buttonVariants } from "~/components/ui/button";
import { cn } from "~/lib/utils";
</script>

<template>
  <div>
    <h1>Hello World</h1>
    <NuxtLink :class="cn(buttonVariants({ variant: 'outline' }))">
      Click me
    </NuxtLink>
    <Button>Click me</Button>
  </div>
</template>
