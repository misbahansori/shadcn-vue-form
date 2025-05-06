<script setup lang="ts" generic="TValue">
import { cn } from "@/lib/utils";
import { type CheckboxGroupProps, useCheckboxGroup } from "@formwerk/core";
import { type HTMLAttributes } from "vue";
import {
  formDescriptionClass,
  formErrorMessageClass,
  formLabelClass,
} from "./config";

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
  <div v-bind="groupProps" class="space-y-2">
    <label v-bind="labelProps" :class="cn(formLabelClass, props.class)">
      <slot name="label">{{ label }}</slot>
    </label>

    <div class="space-y-2">
      <slot />
    </div>

    <div
      v-if="errorMessage"
      v-bind="errorMessageProps"
      :class="formErrorMessageClass"
    >
      {{ errorMessage }}
    </div>

    <div
      v-if="description"
      v-bind="descriptionProps"
      :class="formDescriptionClass"
    >
      {{ description }}
    </div>
  </div>
</template>
