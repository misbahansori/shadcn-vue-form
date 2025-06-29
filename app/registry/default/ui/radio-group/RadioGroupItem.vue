<script setup lang="ts">
import { type RadioProps, useRadio } from "@formwerk/core";
import { type HTMLAttributes } from "vue";

const props = defineProps<
  RadioProps & {
    class?: HTMLAttributes["class"];
  }
>();

const { labelProps, inputProps } = useRadio(props);
</script>

<template>
  <div
    v-bind="inputProps"
    class="group flex items-center gap-2 focus:outline-none"
  >
    <div
      class="border-input group-aria-checked:bg-primary group-aria-checked:text-primary-foreground group-aria-checked:border-primary group-focus:border-ring group-focus:ring-ring/50 aria-invalid:ring-destructive/20 dark:aria-invalid:ring-destructive/40 aria-invalid:border-destructive flex aspect-square size-4 shrink-0 items-center justify-center rounded-full border shadow-xs transition-shadow outline-none group-focus:ring-[3px] disabled:cursor-not-allowed disabled:opacity-50"
    >
      <div
        class="bg-foreground group-aria-checked:bg-background size-1.5 rounded-full opacity-0 group-aria-checked:opacity-100"
      ></div>
    </div>
    <label
      v-bind="labelProps"
      class="text-sm leading-none font-medium peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
    >
      <slot name="label">{{ label }}</slot>
    </label>
  </div>
</template>
