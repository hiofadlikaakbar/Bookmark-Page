<template>
  <div class="container mx-auto px-5 mt-20 lg:mt-32 pb-32">
    <div id="title-extension" class="text-center mb-16">
      <h1 class="text-vdBlue text-2xl md:text-3xl lg:text-4xl font-medium mb-7">
        {{ details.extensionTitle }}
      </h1>
      <p
        class="text-base md:text-lg lg:text-xl max-w-xl lg:max-w-2xl mx-auto text-grayishBlue"
      >
        {{ details.extensionDesc }}
      </p>
    </div>

    <!-- browsers list -->
    <div
      class="grid grid-cols-1 gap-9 lg:grid-cols-3 md:max-w-lg lg:max-w-none mx-auto items-center"
      id="extension"
    >
      <div
        v-for="(browser, index) in details.browsers"
        :key="index"
        class="extension-browser"
        :class="[
          'shadow-2xl pb-6 rounded-md',
          {
            'lg:translate-y-20': index === 1,
            'lg:translate-y-28': index === 2,
          },
        ]"
      >
        <div class="p-6">
          <img
            :src="browser.src"
            :alt="browser.alt"
            class="mx-auto mb-6 scale-95"
          />
          <h1 class="text-vdBlue text-center mb-3 font-semibold text-2xl">
            {{ browser.title }}
          </h1>
          <p class="text-grayishBlue text-center text-base mb-5">
            {{ browser.info }}
          </p>
        </div>
        <img :src="details.dot" :alt="details.dotAlt" class="w-full mb-8" />
        <div>
          <button
            class="px-7 mx-auto py-3 block hover:text-softBlue border-softBlue border duration-300 ease-in-out hover:bg-white rounded-md bg-softBlue text-white"
          >
            {{ details.installButton }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import gsap from "gsap";
import TextPlugin from "gsap/TextPlugin";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(TextPlugin, ScrollTrigger);

import { onMounted } from "vue";
const props = defineProps({
  details: {
    type: Object,
    required: true,
  },
});

onMounted(() => {
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: "#title-extension",
      start: "top center",
      end: "bottom center",
      scrub: 1,
      once: true,
    },
  });

  tl.from("#title-extension", {
    opacity: 0,
    y: 50,
    ease: "slow",
    duration: 3,
  });

  gsap.from(".extension-browser", {
    scrollTrigger: {
      trigger: "#extension",
      start: "top center+=50",
      end: "bottom center",
      scrub: 1,
      once: true,
    },
    opacity: 0,
    y: 50,
    stagger: 0.1,
    duration: 1,
    ease: "back",
  });
});
</script>
