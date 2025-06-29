<script setup lang="ts">
import { cn } from "@/lib/utils";
import { type TextFieldProps, useTextField } from "@formwerk/core";
import { computed, type HTMLAttributes } from "vue";

const props = defineProps<
  TextFieldProps & {
    class?: HTMLAttributes["class"];
    rows?: number;
  }
>();

const {
  inputProps,
  labelProps,
  errorMessage,
  errorMessageProps,
  descriptionProps,
} = useTextField(props);

const delegatedProps = computed(() => {
  const { class: _, ...delegated } = props;
  return delegated;
});
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

    <textarea
      v-bind="inputProps"
      :rows="rows"
      :class="
        cn(
          'border-input placeholder:text-muted-foreground/70 focus-visible:border-ring focus-visible:ring-ring/50 aria-invalid:ring-destructive/20 dark:aria-invalid:ring-destructive/40 aria-invalid:border-destructive flex min-h-19.5 w-full rounded-md border bg-transparent px-3 py-2 text-sm shadow-xs transition-[color,box-shadow] outline-none focus-visible:ring-[3px] disabled:cursor-not-allowed disabled:opacity-50',
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
