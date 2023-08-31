<script setup lang="ts">
type Tech = 'vue' | 'react' | 'nextjs' | 'express' | 'spring' | 'ts' | 'js'

const props = defineProps<{
  href: string
  title: string
  icon?: string
  desc: string
  tech: Tech[]
  delay?: number
  slide: 'left' | 'right'
}>()
</script>

<template>
  <a :href="props.href" target="_blank" :class="`card slide-from-${props.slide}`" :style="`--delay: ${props.delay || 0}ms;`">
    <div class="w-16 min-w-[64px] h-16 flex justify-center">
      <img v-if="props.icon" :src="props.icon" :alt="`${props.title} Logo`" class="max-w-[64px] max-h-[64px]"/>
      <slot></slot>
    </div>
    <div class="ml-4">
      <div class="flex gap-1 items-end">
        <h4 class="text-lg sm:text-xl font-bold mr-2" v-text="props.title"></h4>
        <span class="hidden"> - </span>
        <img v-if="tech.includes('vue')" src="/imgs/tech/vue.svg" alt="Vue Logo" title="VueJS" class="h-4 mb-1"/>
        <img v-if="tech.includes('react')" src="/imgs/tech/react.svg" alt="React Logo" title="React JS" class="h-4 mb-1"/>
        <img v-if="tech.includes('js')" src="/imgs/tech/js.svg" alt="Unofficial JavaScript Logo" title="JavaScript" class="h-4 mb-1"/>
        <img v-if="tech.includes('ts')" src="/imgs/tech/ts.svg" alt="TypeScript Logo" title="TypeScript" class="h-4 mb-1"/>
        <img v-if="tech.includes('nextjs')" src="/imgs/tech/nextjs.svg" alt="Next.js Logo" title="Next.js" class="h-4 mb-1"/>
        <img v-if="tech.includes('express')" src="/imgs/tech/expressjs.svg" alt="ExpressJS Logo" title="ExpressJS" class="h-4 mb-1 dark:hidden"/>
        <img v-if="tech.includes('express')" src="/imgs/tech/expressjs-dark.svg" alt="ExpressJS Logo" title="ExpressJS" class="h-4 mb-1 hidden dark:block"/>
        <img v-if="tech.includes('spring')" src="/imgs/tech/spring.svg" alt="Spring Logo" title="Java Spring" class="h-4 mb-1"/>
      </div>
      <div class="leading-tight" v-text="props.desc"></div>
    </div>
  </a>
</template>

<style>
.card {
  @apply flex px-2 py-2 w-full max-w-sm bg-light-200 dark:bg-dark-600 rounded-lg shadow-lg hover:scale-[0.98] hover:shadow-md transition-transform;
}
.slide-from-left {
  animation: slide-from-left 1000ms cubic-bezier(0.190, 1.000, 0.220, 1.000) var(--delay, 0ms) backwards;
}

.slide-from-right {
  animation: slide-from-right 1000ms cubic-bezier(0.190, 1.000, 0.220, 1.000) var(--delay, 0ms) backwards;
}

@keyframes slide-from-left {
  from {
    opacity: 0;
    transform: translateX(-100%);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slide-from-right {
  from {
    opacity: 0;
    transform: translateX(100%);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>
