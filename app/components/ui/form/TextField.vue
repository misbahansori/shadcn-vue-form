<script setup lang="ts">
import { cn } from "@/lib/utils";
import { type TextFieldProps, useTextField } from "@formwerk/core";
import { type HTMLAttributes } from "vue";
import {
  formDescriptionClass,
  formErrorMessageClass,
  formInputClass,
  formLabelClass,
} from "./config";

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
  <div class="space-y-2">
    <label v-bind="labelProps" :class="cn(formLabelClass, props.class)">
      <slot name="label">{{ label }}</slot>
    </label>

    <input v-bind="inputProps" :class="cn(formInputClass, props.class)" />

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
