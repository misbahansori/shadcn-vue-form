<script setup lang="ts">
import { cn } from "@/lib/utils";
import { type NumberFieldProps, useNumberField } from "@formwerk/core";
import { LucideChevronDown, LucideChevronUp } from "lucide-vue-next";
import { type HTMLAttributes } from "vue";

const props = defineProps<
  NumberFieldProps & {
    class?: HTMLAttributes["class"];
  }
>();

const {
  inputProps,
  labelProps,
  errorMessage,
  errorMessageProps,
  descriptionProps,
  incrementButtonProps,
  decrementButtonProps,
} = useNumberField(props);
</script>

<template>
  <div class="flex flex-col gap-2">
    <label
      v-bind="labelProps"
      :class="
        cn(
          'text-sm leading-none font-medium peer-disabled:cursor-not-allowed peer-disabled:opacity-70',
          props.class,
        )
      "
    >
      <slot name="label">{{ label }}</slot>
    </label>

    <div
      class="border-input focus-within:border-ring focus-within:ring-ring/50 focus-within:has-aria-invalid:ring-destructive/20 dark:focus-within:has-aria-invalid:ring-destructive/40 focus-within:has-aria-invalid:border-destructive relative inline-flex h-9 w-full items-center overflow-hidden rounded-md border text-sm whitespace-nowrap shadow-xs transition-[color,box-shadow] outline-none focus-within:ring-[3px] data-disabled:opacity-50"
    >
      <input
        v-bind="inputProps"
        :class="
          cn(
            'border-input bg-background text-foreground flex-1 px-3 py-2 tabular-nums focus:outline-none',
            props.class,
          )
        "
      />
      <div class="flex h-[calc(100%+2px)] flex-col">
        <button
          type="button"
          v-bind="incrementButtonProps"
          class="border-input bg-background text-muted-foreground/80 hover:bg-accent hover:text-foreground m-0 -me-px flex aspect-square h-1/2 w-6 flex-1 items-center justify-center rounded-none border text-sm transition-[color,box-shadow] disabled:pointer-events-none disabled:cursor-not-allowed disabled:opacity-50"
        >
          <LucideChevronUp :size="12" aria-hidden="true" />
        </button>
        <button
          type="button"
          v-bind="decrementButtonProps"
          class="border-input bg-background text-muted-foreground/80 hover:bg-accent hover:text-foreground m-0 -me-px -mt-px flex aspect-square h-1/2 w-6 flex-1 items-center justify-center rounded-none border text-sm transition-[color,box-shadow] disabled:pointer-events-none disabled:cursor-not-allowed disabled:opacity-50"
        >
          <LucideChevronDown :size="12" aria-hidden="true" />
        </button>
      </div>
    </div>

    <div
      v-if="errorMessage"
      v-bind="errorMessageProps"
      :class="cn('text-destructive text-sm', props.class)"
    >
      {{ errorMessage }}
    </div>

    <div
      v-if="description"
      v-bind="descriptionProps"
      :class="cn('text-muted-foreground text-sm', props.class)"
    >
      {{ description }}
    </div>
  </div>
</template>
