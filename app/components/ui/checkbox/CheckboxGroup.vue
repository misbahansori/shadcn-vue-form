<script setup lang="ts" generic="TValue">
import { cn } from "@/lib/utils";
import { type CheckboxGroupProps, useCheckboxGroup } from "@formwerk/core";
import { type HTMLAttributes } from "vue";

const props = defineProps<
  CheckboxGroupProps<TValue> & {
    class?: HTMLAttributes["class"];
  }
>();

const {
  groupProps,
  labelProps,
  descriptionProps,
  errorMessageProps,
  errorMessage,
  isTouched,
} = useCheckboxGroup(props);
</script>

<template>
  <div v-bind="groupProps" class="flex flex-col gap-2">
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

    <div class="space-y-2">
      <slot />
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
