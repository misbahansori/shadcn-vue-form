<script setup lang="ts">
import { TextArea, TextField } from "@/components/ui/form";

useSeoMeta({
  title: "Shadcn Vue Form - Beautiful Form Components",
  description:
    "A collection of beautiful form components built with Vue and Tailwind CSS.",
  ogTitle: "Shadcn Vue Form - Beautiful Form Components",
  ogDescription:
    "A collection of beautiful form components built with Vue and Tailwind CSS.",
  twitterTitle: "Shadcn Vue Form - Beautiful Form Components",
  twitterDescription:
    "A collection of beautiful form components built with Vue and Tailwind CSS.",
  twitterCard: "summary_large_image",
});
</script>

<template>
  <div class="container mx-auto py-10">
    <div class="max-w-3xl max-sm:text-center">
      <h1
        class="font-heading text-foreground mb-4 text-4xl/[1.1] font-bold tracking-tight md:text-5xl/[1.1]"
      >
        Beautiful Form Components built with
        <span class="text-[#41B883]">Vue</span>
      </h1>
      <p class="text-muted-foreground mb-8 text-lg">
        A collection of beautiful form components built with Vue and Tailwind
        CSS.
      </p>
    </div>

    <div class="mt-16 space-y-8">
      <!-- TextField Section -->
      <div class="space-y-4">
        <h2 class="text-2xl font-bold">Text Field Component</h2>
        <p class="text-muted-foreground">
          A versatile text input component that supports various input types and
          validation.
        </p>
      </div>

      <div class="max-w-md">
        <TextField
          name="username"
          label="Username"
          placeholder="Enter your username"
          description="This is your public display name"
        />
      </div>

      <!-- TextArea Section -->
      <div class="mt-16 space-y-4">
        <h2 class="text-2xl font-bold">Text Area Component</h2>
        <p class="text-muted-foreground">
          A multi-line text input component for longer form content.
        </p>
      </div>

      <div class="max-w-md">
        <TextArea
          name="bio"
          label="Bio"
          placeholder="Tell us about yourself"
          description="Write a short bio about yourself"
          :rows="4"
        />
      </div>
    </div>
  </div>
</template>
