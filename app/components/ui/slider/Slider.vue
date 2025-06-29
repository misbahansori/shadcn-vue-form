<script setup lang="ts">
import { cn } from "@/lib/utils";
import { useSlider, type SliderProps } from "@formwerk/core";
import { type HTMLAttributes } from "vue";
import SliderThumb from "./SliderThumb.vue";

const props = defineProps<
  SliderProps & {
    class?: HTMLAttributes["class"];
  }
>();

const {
  trackProps,
  groupProps,
  labelProps,
  errorMessage,
  errorMessageProps,
  useThumbMetadata,
} = useSlider(props);

const thumbData = useThumbMetadata(0);
</script>

<template>
  <div :class="cn('flex flex-col gap-2', props.class)" v-bind="groupProps">
    <label
      v-bind="labelProps"
      :class="
        cn(
          'text-sm leading-none font-medium peer-disabled:cursor-not-allowed peer-disabled:opacity-70',
        )
      "
    >
      <slot name="label">{{ label }}</slot>
    </label>

    <div
      v-bind="trackProps"
      :class="
        cn(
          'relative flex w-full touch-none items-center select-none data-[disabled]:opacity-50',
          props.orientation === 'vertical'
            ? 'h-full min-h-44 w-auto flex-col'
            : 'h-2 w-full',
        )
      "
    >
      <div
        :class="
          cn(
            'bg-muted relative my-1 grow overflow-hidden rounded-full',
            props.orientation === 'vertical' ? 'h-full w-1.5' : 'h-1.5 w-full',
          )
        "
      >
        <div
          :class="
            cn(
              'bg-primary absolute',
              props.orientation === 'vertical'
                ? 'h-full w-full'
                : 'h-full w-full',
            )
          "
          :style="{ width: `${thumbData.percent * 100}%` }"
        />
      </div>
      <SliderThumb />
    </div>

    <div
      v-if="errorMessage"
      v-bind="errorMessageProps"
      :class="cn('text-destructive text-sm', props.class)"
    >
      {{ errorMessage }}
    </div>
  </div>
</template>
