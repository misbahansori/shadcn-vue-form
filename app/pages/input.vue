<script setup lang="ts">
import { Input } from "~/registry/default/ui/input";
</script>

<template>
  <div class="mb-16">
    <h1
      class="font-heading text-foreground mb-3 text-4xl/[1.1] font-bold tracking-tight md:text-5xl/[1.1]"
    >
      Input
    </h1>
    <p class="text-muted-foreground max-w-3xl text-lg">
      A growing collection of 59 input components built with Vue and Tailwind
      CSS.
    </p>
  </div>
  <div class="grid grid-cols-3 gap-6">
    <div class="flex flex-col justify-between">
      <Input label="Email" />
      <div class="mt-6 flex items-center justify-center text-center">
        <span class="text-muted-foreground text-xs">Text Input with label</span>
      </div>
    </div>
    <div class="flex flex-col justify-between">
      <Input label="Email" description="This is a description" />
      <div class="mt-6 flex items-center justify-center text-center">
        <span class="text-muted-foreground text-xs">
          Text Input with label and description
        </span>
      </div>
    </div>
    <div class="flex flex-col justify-between">
      <Input label="Email" disabled />
      <div class="mt-6 flex items-center justify-center text-center">
        <span class="text-muted-foreground text-xs">
          Text Input with label and disabled
        </span>
      </div>
    </div>
    <div class="flex flex-col justify-between">
      <Input label="Email" required disableHtmlValidation />
      <div class="mt-6 flex items-center justify-center text-center">
        <span class="text-muted-foreground text-xs">
          Text Input with label and required
        </span>
      </div>
    </div>
    <div class="flex flex-col justify-between">
      <Input label="Email" required />
      <div class="mt-6 flex items-center justify-center text-center">
        <span class="text-muted-foreground text-xs">
          Text Input with label and validation error
        </span>
      </div>
    </div>
    <div class="flex flex-col justify-between">
      <Input label="Email" required>
        <template #trailing>
          <div class="text-muted-foreground text-xs">
            <span class="text-destructive">*</span>
          </div>
        </template>
      </Input>
      <div class="mt-6 flex items-center justify-center text-center">
        <span class="text-muted-foreground text-xs">
          Text Input with label and validation error
        </span>
      </div>
    </div>
  </div>
</template>
