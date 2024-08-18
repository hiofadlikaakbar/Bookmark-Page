<template>
  <div class="container mx-auto px-5 py-8">
    <div
      id="footer-detail"
      class="flex flex-col md:flex-row items-center justify-center md:justify-between gap-10"
    >
      <div class="flex-col md:flex-row flex items-center gap-10 lg:gap-16">
        <img
          :src="details.src"
          :alt="details.alt"
          class="mb-8 md:mb-0 scale-100"
        />
        <ul class="text-center flex flex-col md:flex-row gap-5 lg:gap-10">
          <li v-for="(link, index) in details.links" :key="index">
            <a
              :href="link.href"
              class="text-gray-100 hover:text-softRed duration-200 ease-in-out text-base"
              >{{ link.label }}</a
            >
          </li>
        </ul>
      </div>

      <div class="flex gap-7">
        <div
          class="hover:-translate-y-1 duration-200 ease-in-out cursor-pointer"
        >
          <img :src="details.fb" alt="facebook" />
        </div>
        <div
          class="hover:-translate-y-1 duration-200 ease-in-out cursor-pointer"
        >
          <img :src="details.twt" alt="tweeter" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import gsap from "gsap";
import { onMounted } from "vue";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

const props = defineProps({
  details: {
    type: Object,
    required: true,
  },
});

onMounted(() => {
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: "#footer-detail",
      start: "bottom bottom",
      end: "bottom bottom",
      scrub: 1,

      once: true,
    },
  });

  tl.from("#footer-detail", {
    opacity: 0,
    x: -50,
    ease: "slow",
    duration: 3,
  });
});
</script>
