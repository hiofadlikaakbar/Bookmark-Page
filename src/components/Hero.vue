<template>
  <div class="container hero mx-auto mb-28">
    <div
      class="flex flex-col lg:mt-10 lg:flex-row justify-between items-center px-5 xl:px-16"
    >
      <div id="image" class="lg:w-1/2 lg:order-2">
        <img
          :src="details.src"
          :alt="details.alt"
          class="-translate-y-3 xs:-translate-y-0 lg:translate-x-6 mb-20 lg:mb-0 mx-auto xs:scale-110 lg:scale-100"
        />
      </div>
      <div class="lg:w-1/2 lg:order-1">
        <h1
          id="title"
          class="text-2xl xs:text-3xl md:text-4xl text-center lg:text-left xl:text-5xl font-bold text-vdBlue mb-8"
        >
          {{ details.heroTitle }}
        </h1>
        <p
          id="desc"
          class="text-base md:text-lg text-grayishBlue text-center xl:text-xl xl:max-w-lg lg:text-left mb-8"
        ></p>
        <div
          id="button"
          class="flex items-center justify-center lg:justify-start gap-7 xs:gap-4 md:gap-8 xl:gap-6"
        >
          <button
            class="px-2 xs:px-3 py-3 rounded-md border border-softBlue hover:bg-white hover:text-softBlue duration-300 ease-in-out font-medium text-xs xs:text-base whitespace-nowrap bg-softBlue text-white"
          >
            {{ details.buttonChrome }}
          </button>
          <button
            class="px-2 xs:px-3 py-3 rounded-md hover:bg-vdBlue hover:text-white duration-300 ease-in-out bg-white text-xs xs:text-base font-medium whitespace-nowrap text-grayishBlue shadow-md"
          >
            {{ details.buttonFirefox }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import gsap from "gsap";
import TextPlugin from "gsap/TextPlugin";
gsap.registerPlugin(TextPlugin);

import { onMounted } from "vue";
const props = defineProps({
  details: {
    type: Object,
    required: true,
  },
});
onMounted(() => {
  const tl = gsap.timeline();
  tl.from("#image", {
    ease: "back",
    duration: 1,
    y: "120",
    scale: 2,
    opacity: 0,
    rotate: "60",
  });

  tl.from("#title", {
    ease: "power3.inOut",
    duration: 1,
    x: "-120",
    opacity: 0,
  });

  tl.to("#desc", {
    duration: 2,
    ease: "power1.in",
    text: "A clean and simple interface to organize your favourite websites. Open a new browser tab and see your sites load instantly. Try it for free.",
  });

  tl.from("#button", {
    ease: "elastic",
    duration: 1.5,
    y: "-50",
    opacity: 0,
  });
});
</script>
