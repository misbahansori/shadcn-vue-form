<script setup lang="ts">
import { cn } from "@/lib/utils";
import { useSliderThumb, type SliderThumbProps } from "@formwerk/core";
import { type HTMLAttributes } from "vue";

const props = defineProps<
  SliderThumbProps & {
    class?: HTMLAttributes["class"];
  }
>();

const { thumbProps } = useSliderThumb(props);
</script>

<template>
  <div
    v-bind="thumbProps"
    :class="
      cn(
        'border-primary bg-background ring-ring/50 block size-4 shrink-0 rounded-full border shadow-sm transition-[color,box-shadow] outline-none hover:ring-4 focus-visible:ring-4 disabled:pointer-events-none disabled:opacity-50',
        props.class,
      )
    "
  />
</template>
