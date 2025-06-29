<script setup lang="ts">
import { Checkbox, CheckboxGroup } from "@/components/ui/checkbox";
import { Input } from "~/components/ui/input";
import { NumberField } from "~/components/ui/number-field";
import { RadioGroup, RadioGroupItem } from "~/components/ui/radio-group";
import { Select, SelectOption } from "~/components/ui/select";
import { Slider } from "~/components/ui/slider";
import { Switch } from "~/components/ui/switch";
import { Textarea } from "~/components/ui/textarea";

useSeoMeta({
  title: "Shadcn Vue Form - Beautiful Form Components",
  description:
    "A collection of beautiful form components built with Vue and Tailwind CSS.",
  ogTitle: "Shadcn Vue Form - Beautiful Form Components",
  ogDescription:
    "A collection of beautiful form components built with Vue and Tailwind CSS.",
  twitterTitle: "Shadcn Vue Form - Beautiful Form Components",
  twitterDescription:
    "A collection of beautiful form components built with Vue and Tailwind CSS.",
  twitterCard: "summary_large_image",
});
</script>

<template>
  <div class="container mx-auto py-10">
    <div class="max-w-3xl max-sm:text-center">
      <h1
        class="font-heading text-foreground mb-4 text-4xl/[1.1] font-bold tracking-tight md:text-5xl/[1.1]"
      >
        Beautiful Form Components built with
        <span class="text-[#41B883]">Vue</span>
      </h1>
      <p class="text-muted-foreground mb-8 text-lg">
        A collection of beautiful form components built with Vue and Tailwind
        CSS.
      </p>
    </div>

    <div class="grid grid-cols-1 gap-8 md:grid-cols-2">
      <div>
        <div class="space-y-4">
          <h2 class="text-2xl font-bold">Text Field Component</h2>
          <p class="text-muted-foreground">
            A versatile text input component that supports various input types
            and validation.
          </p>
        </div>

        <div class="mt-4">
          <Input
            label="Username"
            name="username"
            placeholder="Enter your username"
            description="This is your public display name"
          />
        </div>
      </div>

      <div>
        <div class="space-y-4">
          <h2 class="text-2xl font-bold">Text Area Component</h2>
          <p class="text-muted-foreground">
            A multi-line text input component for longer form content.
          </p>
        </div>

        <div class="mt-4">
          <Textarea
            name="bio"
            label="Bio"
            placeholder="Tell us about yourself"
            description="Write a short bio about yourself"
            :rows="4"
          />
        </div>
      </div>

      <div>
        <div class="space-y-4">
          <h2 class="text-2xl font-bold">Number Field Component</h2>
          <p class="text-muted-foreground">
            A number input component with increment/decrement controls.
          </p>
        </div>

        <div class="mt-4">
          <NumberField
            name="amount"
            label="Amount"
            :min="0"
            :max="100"
            :step="1"
            description="Enter an amount between 0 and 100"
          />
        </div>
      </div>

      <div>
        <div class="space-y-4">
          <h2 class="text-2xl font-bold">Radio Group Component</h2>
          <p class="text-muted-foreground">
            A group of radio buttons for selecting a single option.
          </p>
        </div>

        <div class="mt-4">
          <RadioGroup
            name="options"
            label="Select an option"
            description="Choose one of the following options"
          >
            <RadioGroupItem value="1" label="Option 1" />
            <RadioGroupItem value="2" label="Option 2" />
            <RadioGroupItem value="3" label="Option 3" />
          </RadioGroup>
        </div>
      </div>

      <div>
        <div class="space-y-4">
          <h2 class="text-2xl font-bold">Checkbox Component</h2>
          <p class="text-muted-foreground">
            A single checkbox for binary choices.
          </p>
        </div>

        <div class="mt-4">
          <Checkbox
            name="terms"
            label="I accept the terms and conditions"
            description="You must accept the terms to continue"
          />
        </div>
      </div>

      <div>
        <div class="space-y-4">
          <h2 class="text-2xl font-bold">Checkbox Group Component</h2>
          <p class="text-muted-foreground">
            A group of checkboxes for selecting multiple options.
          </p>
        </div>

        <div class="mt-4">
          <CheckboxGroup
            name="preferences"
            label="Select your preferences"
            description="Choose all that apply"
          >
            <Checkbox value="newsletter" label="Subscribe to newsletter" />
            <Checkbox value="updates" label="Receive updates" />
            <Checkbox value="marketing" label="Marketing emails" />
          </CheckboxGroup>
        </div>
      </div>

      <div>
        <div class="space-y-4">
          <h2 class="text-2xl font-bold">Select Component</h2>
          <p class="text-muted-foreground">
            A dropdown select component for choosing from a list of options.
          </p>
        </div>

        <div class="mt-4">
          <Select
            name="country"
            label="Select Country"
            placeholder="Choose a country"
            description="Select your country of residence"
          >
            <SelectOption value="us" label="United States" />
            <SelectOption value="uk" label="United Kingdom" />
            <SelectOption value="ca" label="Canada" />
            <SelectOption value="au" label="Australia" />
          </Select>
        </div>
      </div>

      <div>
        <div class="space-y-4">
          <h2 class="text-2xl font-bold">Slider Component</h2>
          <p class="text-muted-foreground">
            A slider component for selecting values within a range.
          </p>
        </div>

        <div class="mt-4">
          <Slider
            name="volume"
            label="Volume"
            :min="0"
            :max="100"
            :step="1"
            :model-value="50"
          />
        </div>
      </div>

      <div>
        <div class="space-y-4">
          <h2 class="text-2xl font-bold">Switch Component</h2>
          <p class="text-muted-foreground">
            A switch component for toggling boolean values.
          </p>
        </div>

        <div class="mt-4">
          <Switch name="notifications" label="Enable notifications" />
        </div>
      </div>
    </div>
  </div>
</template>
