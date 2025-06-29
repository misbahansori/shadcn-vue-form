# Shadcn Vue Form - Beautiful Form Components

A collection of beautiful form components built with Vue, Tailwind CSS, and Formwerk. This project showcases modern form components that are accessible, customizable, and ready for production use.

## Features

- [Nuxt v3](https://nuxt.com/) - The intuitive Vue framework
- [Tailwind CSS v4](https://tailwindcss.com/) - A utility-first CSS framework
- [shadcn-vue](https://www.shadcn-vue.com/) - Re-usable components built with Reka UI and Tailwind CSS
- [Formwerk](https://formwerk.dev/) - Modern form library for Vue with validation and accessibility
- [Reka UI](https://reka-ui.com/) - Unstyled, accessible components for building high-quality design systems
- [Prettier](https://prettier.io/) - Opinionated code formatter

## Form Components

This project includes a comprehensive set of form components built with Formwerk and styled with shadcn-vue:

- **Text Fields** - Input components with validation and accessibility
- **Number Fields** - Numeric inputs with formatting and step controls
- **Radio Groups** - Single selection from multiple options
- **Checkboxes** - Binary and multi-selection components
- **Select Fields** - Dropdown selection components
- **Sliders** - Range selection with visual feedback
- **Textareas** - Multi-line text inputs
- **And more...**

## Setup

Make sure to install the dependencies:

```bash
pnpm install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
pnpm dev
```

## Production

Build the application for production:

```bash
pnpm build
```

Locally preview production build:

```bash
pnpm preview
```

## Usage

### Basic Form Component Usage

```vue
<template>
  <Input
    name="username"
    label="Username"
    placeholder="Enter your username"
    description="This is your public display name"
  />
</template>

<script setup>
import { Input } from "~/components/ui/input";
</script>
```

### Slider Component with Formwerk

```vue
<template>
  <Slider
    name="volume"
    label="Volume"
    :min="0"
    :max="100"
    :step="1"
    :model-value="50"
  />
</template>

<script setup>
import { Slider } from "~/components/ui/slider";
</script>
```

### Form Validation with Formwerk

```vue
<template>
  <Input
    name="email"
    label="Email"
    :schema="emailSchema"
    placeholder="Enter your email"
  />
</template>

<script setup>
import { z } from "zod";
import { Input } from "~/components/ui/input";

const emailSchema = z.string().email("Please enter a valid email");
</script>
```

## Component Structure

```
app/components/ui/
├── button/          # Button components
├── checkbox/        # Checkbox and checkbox group
├── input/           # Text input fields
├── number-field/    # Numeric input fields
├── radio-group/     # Radio button groups
├── select/          # Dropdown select components
├── slider/          # Range slider components
├── textarea/        # Multi-line text inputs
└── ...
```

## Customization

- **Tailwind CSS**: Customize your design tokens in the `app/assets/css/tailwind.css` file
- **Formwerk**: Configure validation schemas and form behavior
- **shadcn-vue**: Modify or add components in the `app/components/ui/` directory
- **Nuxt configuration**: Adjust the Nuxt settings in the `nuxt.config.ts` file

## Formwerk Integration

This project uses [Formwerk](https://formwerk.dev/) for form handling, validation, and accessibility. Formwerk provides:

- **Built-in validation** with support for Zod, Valibot, and other schema validators
- **Accessibility features** with proper ARIA attributes and keyboard navigation
- **Type safety** with full TypeScript support
- **Flexible composables** for building custom form components

## Learn More

To learn more about the technologies used in this project, check out the following resources:

- [Formwerk Documentation](https://formwerk.dev/) - Modern form library for Vue
- [shadcn-vue Documentation](https://www.shadcn-vue.com/docs/introduction.html) - Component library
- [Nuxt 3 Documentation](https://nuxt.com/docs/getting-started/introduction) - Vue framework
- [Tailwind CSS Documentation](https://tailwindcss.com/docs) - CSS framework
- [Reka UI Documentation](https://reka-ui.com/docs/overview/getting-started) - Component primitives

## Deploy

Deploy your form application easily with platforms like [Vercel](https://vercel.com/), [Netlify](https://www.netlify.com/), [Cloudflare Pages](https://pages.cloudflare.com/) or [NuxtHub](https://hub.nuxt.com/).

Check out the [Nuxt deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.

## License

[MIT License](LICENSE)
