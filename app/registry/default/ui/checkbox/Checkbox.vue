<script setup lang="ts" generic="TValue">
import { type CheckboxProps, useCheckbox } from "@formwerk/core";
import { type HTMLAttributes } from "vue";

const props = defineProps<
  CheckboxProps<TValue> & {
    class?: HTMLAttributes["class"];
  }
>();

const { labelProps, inputProps, isChecked } = useCheckbox(props);
</script>

<template>
  <div
    v-bind="inputProps"
    class="group flex items-center gap-2 focus:outline-none"
  >
    <div
      class="border-input group-aria-checked:bg-primary group-aria-checked:text-primary-foreground group-aria-checked:border-primary group-focus:border-ring group-focus:ring-ring/50 aria-invalid:ring-destructive/20 dark:aria-invalid:ring-destructive/40 aria-invalid:border-destructive flex aspect-square size-4 shrink-0 items-center justify-center rounded-[4px] border shadow-xs transition-shadow outline-none group-focus:ring-[3px] disabled:cursor-not-allowed disabled:opacity-500"
    >
      <svg
        v-if="isChecked"
        width="9"
        height="9"
        viewBox="0 0 9 9"
        fill="currentcolor"
        xmlns="http://www.w3.org/2000/svg"
        class="opacity-0 group-aria-checked:opacity-100"
      >
        <path
          fillRule="evenodd"
          clipRule="evenodd"
          d="M8.53547 0.62293C8.88226 0.849446 8.97976 1.3142 8.75325 1.66099L4.5083 8.1599C4.38833 8.34356 4.19397 8.4655 3.9764 8.49358C3.75883 8.52167 3.53987 8.45309 3.3772 8.30591L0.616113 5.80777C0.308959 5.52987 0.285246 5.05559 0.563148 4.74844C0.84105 4.44128 1.31533 4.41757 1.62249 4.69547L3.73256 6.60459L7.49741 0.840706C7.72393 0.493916 8.18868 0.396414 8.53547 0.62293Z"
        />
      </svg>
    </div>
    <label
      v-bind="labelProps"
      class="text-sm leading-none font-medium peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
    >
      <slot name="label">{{ label }}</slot>
    </label>
  </div>
</template>
