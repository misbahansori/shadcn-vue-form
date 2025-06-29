<script setup lang="ts">
import { cn } from "@/lib/utils";
import { type TextFieldProps, useTextField } from "@formwerk/core";
import { type HTMLAttributes } from "vue";

const props = defineProps<
  TextFieldProps & {
    class?: HTMLAttributes["class"];
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
  <div class="flex flex-col gap-2">
    <label
      v-bind="labelProps"
      class="text-sm leading-none font-medium peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
    >
      <slot name="label">{{ label }}</slot>
      <span v-if="props.required" class="text-destructive">&nbsp;*</span>
    </label>

    <input
      v-bind="inputProps"
      :class="
        cn(
          'border-input placeholder:text-muted-foreground/70 focus-visible:border-ring focus-visible:ring-ring/50 aria-invalid:ring-destructive/20 dark:aria-invalid:ring-destructive/40 aria-invalid:border-destructive flex h-9 w-full min-w-0 rounded-md border bg-transparent px-3 py-1 text-sm shadow-xs transition-[color,box-shadow] outline-none file:inline-flex file:h-7 file:border-0 file:bg-transparent file:text-sm file:font-medium focus-visible:ring-[3px] disabled:pointer-events-none disabled:cursor-not-allowed disabled:opacity-50',
          props.class,
        )
      "
    />

    <div
      v-if="errorMessage"
      v-bind="errorMessageProps"
      :class="cn('text-destructive text-xs', props.class)"
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
