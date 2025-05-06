<script setup lang="ts">
import { cn } from "@/lib/utils";
import { type TextFieldProps, useTextField } from "@formwerk/core";
import { type HTMLAttributes } from "vue";

type SupportedInputType = "text" | "password" | "email" | "tel" | "url";

const props = defineProps<
  TextFieldProps & {
    class?: HTMLAttributes["class"];
    type?: SupportedInputType;
  }
>();

const {
  inputProps,
  labelProps,
  errorMessage,
  errorMessageProps,
  descriptionProps,
} = useTextField(props);
</script>

<template>
  <div class="space-y-2">
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

    <input
      v-bind="inputProps"
      :class="
        cn(
          'border-input file:text-foreground placeholder:text-muted-foreground/70 flex h-9 w-full min-w-0 rounded-md border bg-transparent px-3 py-1 text-sm shadow-xs transition-[color,box-shadow] outline-none file:inline-flex file:h-7 file:border-0 file:bg-transparent file:text-sm file:font-medium disabled:pointer-events-none disabled:cursor-not-allowed disabled:opacity-50',
          'focus-visible:border-ring focus-visible:ring-ring/50 focus-visible:ring-[3px]',
          'aria-invalid:ring-destructive/20 dark:aria-invalid:ring-destructive/40 aria-invalid:border-destructive',
          props.class,
        )
      "
    />

    <div
      v-if="errorMessage"
      v-bind="errorMessageProps"
      class="text-destructive text-sm"
    >
      {{ errorMessage }}
    </div>

    <div
      v-if="description"
      v-bind="descriptionProps"
      class="text-muted-foreground text-sm"
    >
      {{ description }}
    </div>
  </div>
</template>
