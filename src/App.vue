<script setup lang="ts">
import { ref } from 'vue'
import ThemeSwitch from './components/ThemeSwitch.vue'
import Notification from './components/Notification.vue'
import ProjectCard from './components/ProjectCard.vue'

var notification = ref({ success: false, msg: '', time: 0 })
function copyText(text: string) {
  navigator.clipboard.writeText(text)
  notification.value = { msg: text + ' copied to clipboard', success: true, time: Date.now() }
}
</script>

<template>
  <div class="w-full flex flex-col items-center justify-between relative overflow-x-hidden min-h-screen fade-in">
    <div class="fixed w-min top-0 right-0 z-20 m-4">
      <ThemeSwitch></ThemeSwitch>
    </div>
    <div class="flex flex-col items-center py-8 px-4 sm:px-8">
      <div class="flex flex-col items-center">
        <div class="w-32 h-32 relative rounded-full shadow-glow dark:shadow-white hover:shadow-glow-lg transition-shadow overflow-hidden group">
          <img src="/imgs/icon.webp" width="128" height="128" alt="Profile picture" class="absolute"/>
          <img src="/imgs/icon.gif" loading="lazy" width="128" height="128" alt="Profile picture" class="absolute hidden group-hover:block"/>
        </div>
        <div class="mt-2 pb-1 sm:pb-3 lg:pb-5 text-4xl sm:text-7xl lg:text-8xl font-extrabold text-transparent bg-clip-text text-gradient">
          1withspaghetti
        </div>
        <div class="text-sm sm:text-lg sm:-mt-1 whitespace-nowrap">
          Aspiring Web Developer • Highschool Junior • USA
        </div>
      </div>
      <div class="mt-2 flex gap-4">
        <a href="https://github.com/1withspaghetti" target="_blank" title="Github" class="hover:scale-110 transition-transform">
          <svg width="32" height="32" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 98 96" fill="currentColor"><path fill-rule="evenodd" clip-rule="evenodd" d="M48.854 0C21.839 0 0 22 0 49.217c0 21.756 13.993 40.172 33.405 46.69 2.427.49 3.316-1.059 3.316-2.362 0-1.141-.08-5.052-.08-9.127-13.59 2.934-16.42-5.867-16.42-5.867-2.184-5.704-5.42-7.17-5.42-7.17-4.448-3.015.324-3.015.324-3.015 4.934.326 7.523 5.052 7.523 5.052 4.367 7.496 11.404 5.378 14.235 4.074.404-3.178 1.699-5.378 3.074-6.6-10.839-1.141-22.243-5.378-22.243-24.283 0-5.378 1.94-9.778 5.014-13.2-.485-1.222-2.184-6.275.486-13.038 0 0 4.125-1.304 13.426 5.052a46.97 46.97 0 0 1 12.214-1.63c4.125 0 8.33.571 12.213 1.63 9.302-6.356 13.427-5.052 13.427-5.052 2.67 6.763.97 11.816.485 13.038 3.155 3.422 5.015 7.822 5.015 13.2 0 18.905-11.404 23.06-22.324 24.283 1.78 1.548 3.316 4.481 3.316 9.126 0 6.6-.08 11.897-.08 13.526 0 1.304.89 2.853 3.316 2.364 19.412-6.52 33.405-24.935 33.405-46.691C97.707 22 75.788 0 48.854 0z"/></svg>
        </a>
        <a href="#" @click="copyText('1withspaghetti')" title="Discord" class="hover:scale-110 transition-transform">
          <svg width="32" height="32" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 71 55" fill="currentColor"><path d="M60.1045 4.8978C55.5792 2.8214 50.7265 1.2916 45.6527 0.41542C45.5603 0.39851 45.468 0.440769 45.4204 0.525289C44.7963 1.6353 44.105 3.0834 43.6209 4.2216C38.1637 3.4046 32.7345 3.4046 27.3892 4.2216C26.905 3.0581 26.1886 1.6353 25.5617 0.525289C25.5141 0.443589 25.4218 0.40133 25.3294 0.41542C20.2584 1.2888 15.4057 2.8186 10.8776 4.8978C10.8384 4.9147 10.8048 4.9429 10.7825 4.9795C1.57795 18.7309 -0.943561 32.1443 0.293408 45.3914C0.299005 45.4562 0.335386 45.5182 0.385761 45.5576C6.45866 50.0174 12.3413 52.7249 18.1147 54.5195C18.2071 54.5477 18.305 54.5139 18.3638 54.4378C19.7295 52.5728 20.9469 50.6063 21.9907 48.5383C22.0523 48.4172 21.9935 48.2735 21.8676 48.2256C19.9366 47.4931 18.0979 46.6 16.3292 45.5858C16.1893 45.5041 16.1781 45.304 16.3068 45.2082C16.679 44.9293 17.0513 44.6391 17.4067 44.3461C17.471 44.2926 17.5606 44.2813 17.6362 44.3151C29.2558 49.6202 41.8354 49.6202 53.3179 44.3151C53.3935 44.2785 53.4831 44.2898 53.5502 44.3433C53.9057 44.6363 54.2779 44.9293 54.6529 45.2082C54.7816 45.304 54.7732 45.5041 54.6333 45.5858C52.8646 46.6197 51.0259 47.4931 49.0921 48.2228C48.9662 48.2707 48.9102 48.4172 48.9718 48.5383C50.038 50.6034 51.2554 52.5699 52.5959 54.435C52.6519 54.5139 52.7526 54.5477 52.845 54.5195C58.6464 52.7249 64.529 50.0174 70.6019 45.5576C70.6551 45.5182 70.6887 45.459 70.6943 45.3942C72.1747 30.0791 68.2147 16.7757 60.1968 4.9823C60.1772 4.9429 60.1437 4.9147 60.1045 4.8978ZM23.7259 37.3253C20.2276 37.3253 17.3451 34.1136 17.3451 30.1693C17.3451 26.225 20.1717 23.0133 23.7259 23.0133C27.308 23.0133 30.1626 26.2532 30.1066 30.1693C30.1066 34.1136 27.28 37.3253 23.7259 37.3253ZM47.3178 37.3253C43.8196 37.3253 40.9371 34.1136 40.9371 30.1693C40.9371 26.225 43.7636 23.0133 47.3178 23.0133C50.9 23.0133 53.7545 26.2532 53.6986 30.1693C53.6986 34.1136 50.9 37.3253 47.3178 37.3253Z"/></svg>
        </a>
        <a href="mailto:contact@1withspaghetti.com" @click="copyText('contact@1withspaghetti.com')" title="Email" class="hover:scale-110 transition-transform">
          <svg width="32" height="32" xmlns="http://www.w3.org/2000/svg" viewBox="0 96 960 960" fill="currentColor"><path d="M149 921q-39.05 0-66.525-27.475Q55 866.05 55 827V325q0-39.463 27.475-67.231Q109.95 230 149 230h662q39.463 0 67.231 27.769Q906 285.537 906 325v502q0 39.05-27.769 66.525Q850.463 921 811 921H149Zm331-295L149 403v424h662V403L480 626Zm0-83 327-218H154l326 218ZM149 403v-78 502-424Z"/></svg>
        </a>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-8">
        <ProjectCard
          title="Spaghetti Share"
          href="https://share.1withspaghetti.com/"
          icon="imgs/spaghetti-share.webp"
          desc="Image and Video hosting website"
          :tech="['vue', 'express', 'ts']"
          :delay="500"
          slide="left"
        ></ProjectCard>
        <ProjectCard
          title="Hypixel Pit Stats"
          href="https://pit.1withspaghetti.com/"
          icon="imgs/hypixel.webp"
          desc="Simple Minecraft Pit statistics using Hypixel API"
          :tech="['react', 'nextjs', 'ts']"
          :delay="600"
          slide="right"
        ></ProjectCard>

        <ProjectCard
          title="TextureMC"
          href="https://texturemc.com/"
          icon="imgs/texturemc.webp"
          desc="A website for creating Minecraft texture packs"
          :tech="['ts', 'spring']"
          :delay="800"
          slide="left"
        ></ProjectCard>
        <ProjectCard
          title="Wordle Solver 2.0"
          href="https://1withspaghetti.com/projects/wordlesolver/"
          icon="imgs/wordle.png"
          desc="A Bot that automatically solves the popular game of Wordle"
          :tech="['js']"
          :delay="900"
          slide="right"
        ></ProjectCard>

        <ProjectCard
          title="Annoying Sign-up Form"
          href="https://1withspaghetti.com/projects/sign-up-page/"
          desc="An over-complicated questionnaire, designed to frustrate you"
          :tech="['js']"
          :delay="1100"
          slide="left"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="w-full" viewBox="0 0 48 48" fill="currentColor"><path d="M15.95 35.5h16.1v-3h-16.1Zm0-8.5h16.1v-3h-16.1ZM11 44q-1.2 0-2.1-.9Q8 42.2 8 41V7q0-1.2.9-2.1Q9.8 4 11 4h18.05L40 14.95V41q0 1.2-.9 2.1-.9.9-2.1.9Zm16.55-27.7V7H11v34h26V16.3ZM11 7v9.3V7v34V7Z"/></svg>
        </ProjectCard>
      </div>
    </div>
  </div>
  <Notification v-bind="notification" />
</template>

<style>
@keyframes move-bg {
  to {
    background-position: 0 0;
  }
  from {
    background-position: 200% 0;
  }
}
.text-gradient {
  background-size: 200% 100%;
  background-image: linear-gradient(to right, #3c91f9, #1d4ed8, #3c91f9);
  animation: move-bg 5s infinite linear;
}
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
.fade-in {
  animation: fadeIn 500ms ease-in-out;
}
</style>
