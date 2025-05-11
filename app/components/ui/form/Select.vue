<script setup lang="ts">
import { useSelect, type SelectProps } from "@formwerk/core";
import { useId } from "vue";
import {
  formDescriptionClass,
  formErrorMessageClass,
  formLabelClass,
} from "~/components/ui/form/config";

const props = defineProps<SelectProps<string, string>>();

const id = useId();
const triggerId = `--trigger-${id}`;

const {
  triggerProps,
  labelProps,
  errorMessageProps,
  isTouched,
  errorMessage,
  fieldValue,
  listBoxProps,
  descriptionProps,
  isPopupOpen,
} = useSelect(props);
</script>

<template>
  <div class="space-y-2">
    <div v-bind="labelProps" :class="cn(formLabelClass)">
      {{ label }}
    </div>

    <div class="relative">
      <button
        ref="reference"
        v-bind="triggerProps"
        :id="triggerId"
        class="border-input text-foreground data-[placeholder]:text-muted-foreground focus-visible:border-ring focus-visible:ring-ring/50 aria-invalid:ring-destructive/20 dark:aria-invalid:ring-destructive/40 aria-invalid:border-destructive flex h-9 w-full items-center justify-between gap-2 rounded-md border bg-transparent px-3 py-2 text-sm shadow-xs transition-[color,box-shadow] outline-none focus-visible:ring-[3px] disabled:cursor-not-allowed disabled:opacity-50 *:data-[slot=select-value]:flex *:data-[slot=select-value]:items-center *:data-[slot=select-value]:gap-2 [&_svg]:pointer-events-none [&_svg]:shrink-0 [&>span]:line-clamp-1"
      >
        <span class="block truncate">
          {{ fieldValue || placeholder || "Select an option" }}
        </span>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
          class="h-4 w-4 opacity-50"
        >
          <path d="m6 9 6 6 6-6" />
        </svg>
      </button>

      <div
        v-if="isPopupOpen"
        ref="floating"
        v-bind="listBoxProps"
        class="bg-popover text-popover-foreground absolute z-50 min-w-[8rem] overflow-hidden rounded-md border shadow-md"
      >
        <slot />
      </div>
    </div>

    <p
      v-if="description"
      v-bind="descriptionProps"
      :class="cn(formDescriptionClass)"
    >
      {{ description }}
    </p>

    <p
      v-if="isTouched && errorMessage"
      v-bind="errorMessageProps"
      :class="cn(formErrorMessageClass)"
    >
      {{ errorMessage }}
    </p>
  </div>
</template>
