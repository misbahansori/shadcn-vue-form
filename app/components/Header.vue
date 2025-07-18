<script setup lang="ts">
import { buttonVariants } from "@/components/ui/button";
import { cn } from "@/lib/utils";

interface Link {
  text: string;
  href: string;
  isNew?: boolean;
  external?: boolean;
}

const links: Link[] = [
  // { text: "Extended", href: "/extended", isNew: true },
  // { text: "Layouts", href: "/layouts" },
  // { text: "Colors", href: "/colors" },
  // {
  //   text: "Easing Classes",
  //   href: "/easings",
  // },
];

const isMobile = ref(false);

onMounted(() => {
  checkIfMobile();
  window.addEventListener("resize", checkIfMobile);
});

function checkIfMobile() {
  isMobile.value = window.innerWidth < 768;
}
</script>

<template>
  <header
    class="before:bg-[linear-gradient(to_right,--theme(--color-border/.3),--theme(--color-border)_200px,--theme(--color-border)_calc(100%-200px),--theme(--color-border/.3))] relative mb-14 before:absolute before:-inset-x-32 before:bottom-0 before:h-px"
  >
    <div
      class="before:bg-ring/50 after:bg-ring/50 before:absolute before:-bottom-px before:-left-12 before:z-10 before:-ml-px before:size-[3px] after:absolute after:-right-12 after:-bottom-px after:z-10 after:-mr-px after:size-[3px]"
      aria-hidden="true"
    ></div>
    <div
      class="mx-auto flex h-[72px] w-full max-w-6xl items-center justify-between gap-3"
    >
      <NuxtLink
        to="/"
        aria-label="Home"
        class="flex shrink-0 items-center gap-2"
      >
        <div class="font-heading text-[1.4rem] font-semibold">
          Shadcn
          <span class="font-bold text-[#41B883]">Vue</span>
          Form
        </div>
      </NuxtLink>
      <div class="flex items-center">
        <template v-if="!isMobile">
          <div class="flex items-center gap-4 md:gap-10">
            <NuxtLink
              v-for="link in links"
              :key="link.href"
              :to="link.href"
              class="text-muted-foreground hover:text-foreground/80 relative"
              :target="link.external ? '_blank' : '_self'"
              :external="link.external ?? false"
            >
              {{ link.text }}
              <span
                v-if="link.isNew"
                class="bg-primary text-primary-foreground absolute -top-3 -right-6 rounded-full px-1.5 py-0.5 text-[0.6rem] leading-none font-medium"
              >
                NEW
              </span>
            </NuxtLink>
          </div>
          <div
            class="bg-input ms-4 me-4 h-5 w-px md:ms-10"
            aria-hidden="true"
          ></div>
        </template>
        <div class="flex items-center gap-1">
          <a
            :class="
              cn(
                buttonVariants({ variant: 'ghost', size: 'icon' }),
                'text-muted-foreground hover:text-foreground/80',
              )
            "
            href="https://x.com/MisbahAnsori24"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span class="sr-only">X</span>
            <!-- Twitter X Icon -->
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="currentColor"
              width="20"
              height="20"
            >
              <path
                d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"
              ></path>
            </svg>
          </a>
          <a
            :class="
              cn(
                buttonVariants({ variant: 'ghost', size: 'icon' }),
                'text-muted-foreground hover:text-foreground/80',
              )
            "
            href="https://github.com/misbahansori/shadcn-vue-form"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span class="sr-only">GitHub</span>
            <!-- GitHub Icon -->
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="currentColor"
              width="20"
              height="20"
            >
              <path
                d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
              />
            </svg>
          </a>
        </div>
      </div>
    </div>
  </header>
</template>
