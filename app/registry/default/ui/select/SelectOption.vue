<script setup lang="ts">
import { useOption, type OptionProps } from "@formwerk/core";

const props = defineProps<OptionProps<string>>();

const { optionProps, isSelected } = useOption(props);
</script>

<template>
  <div
    v-bind="optionProps"
    class="hover:bg-accent hover:text-accent-foreground relative flex w-full cursor-default items-center rounded-sm py-1.5 pr-2 pl-7 text-sm outline-none select-none data-[disabled]:pointer-events-none data-[disabled]:opacity-50"
  >
    <span
      class="absolute left-1.5 flex h-3.5 w-3.5 items-center justify-center"
    >
      <svg
        v-if="isSelected"
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="h-4 w-4 shrink-0"
      >
        <polyline points="20 6 9 17 4 12" />
      </svg>
    </span>
    <span class="block truncate">{{ label }}</span>
  </div>
</template>
