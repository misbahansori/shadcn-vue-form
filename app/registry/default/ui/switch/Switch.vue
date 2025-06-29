<script setup lang="ts">
import { useSwitch, type SwitchProps } from "@formwerk/core";
import { type HTMLAttributes } from "vue";

const props = defineProps<
  SwitchProps & {
    class?: HTMLAttributes["class"];
  }
>();

const { inputProps, labelProps, isPressed, errorMessage, errorMessageProps } =
  useSwitch(props);
</script>

<template>
  <div class="flex flex-col gap-2">
    <label
      v-bind="labelProps"
      :class="
        cn(
          'group flex items-center gap-2 text-sm leading-none font-medium peer-disabled:cursor-not-allowed peer-disabled:opacity-70',
        )
      "
    >
      <input v-bind="inputProps" type="checkbox" class="peer sr-only" />

      <div
        class="peer-checked:bg-primary bg-input focus-visible:ring-ring/50 inline-flex h-6 w-10 shrink-0 items-center rounded-full border-2 border-transparent transition-all outline-none focus-visible:ring-[3px] disabled:cursor-not-allowed disabled:opacity-50"
      >
        <div
          class="bg-background pointer-events-none block size-5 translate-x-0 rounded-full shadow-xs ring-0 transition-transform group-has-peer-checked:translate-x-4 group-has-peer-checked:rtl:-translate-x-4"
        ></div>
      </div>

      {{ label }}
    </label>

    <div v-bind="errorMessageProps" class="error">
      {{ errorMessage }}
    </div>
  </div>
</template>
