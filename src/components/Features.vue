<template>
  <div class="container mx-auto px-5 mb-20">
    <div id="tab">
      <div class="text-center mb-10">
        <h1
          class="text-vdBlue text-2xl md:text-3xl lg:text-4xl font-medium mb-7"
        >
          {{ details.featureTitle }}
        </h1>
        <p
          class="text-base md:text-lg lg:text-xl lg:max-w-2xl mx-auto text-grayishBlue"
        >
          {{ details.featureDesc }}
        </p>
      </div>
      <div
        class="grid-cols-1 lg:grid-cols-3 max-w-3xl mx-auto grid items-center justify-center"
      >
        <span
          v-for="(feature, index) in details.features"
          :key="index"
          class="border-t border-t-grayishBlue lg:border-none"
        >
          <div
            class="strip-tab relative cursor-pointer"
            @click="changeTab(index)"
          >
            <h1
              class="text-base lg:text-xl text-grayishBlue hover:text-vdBlue duration-500 ease-in-out text-center md:text-lg py-6"
              :class="{ 'text-vdBlue': activeTab === index }"
            >
              {{ feature.title }}
            </h1>
            <span
              v-show="activeTab === index"
              class="w-[130px] md:w-[200px] lg:w-full h-[3px] rounded-full bg-softRed absolute bottom-0 left-1/2 transform -translate-x-1/2"
            ></span>
          </div>
        </span>
      </div>
    </div>
  </div>

  <div class="relative mt-20">
    <div class="feature">
      <div
        id="feature-detail"
        class="flex lg:flex-row px-5 flex-col justify-between items-center"
      >
        <div class="lg:w-1/2">
          <img
            v-for="(feature, index) in details.features"
            :key="index"
            :src="feature.src"
            :alt="feature.alt"
            class="mx-auto md:scale-100 mb-16 lg:mb-0 lg:scale-90"
            v-show="activeTab === index"
          />
        </div>
        <div class="lg:w-[46%]">
          <div
            v-for="(feature, index) in details.features"
            :key="index"
            v-show="activeTab === index"
          >
            <h1
              class="text-vdBlue text-2xl lg:text-left md:text-3xl lg:text-4xl text-center font-medium mb-7"
            >
              {{ feature.title }}
            </h1>
            <p
              class="text-base md:text-lg mb-7 lg:text-left lg:text-xl max-w-lg text-grayishBlue text-center"
            >
              {{ feature.desc }}
            </p>
            <button
              v-show="activeTab === index"
              class="py-3 rounded-md px-7 bg-softBlue border border-softBlue hover:bg-white hover:text-softBlue duration-300 ease-in-out hidden lg:block text-white"
            >
              {{ details.buttonInfo }}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

const props = defineProps({
  details: {
    type: Object,
    required: true,
  },
});
const activeTab = ref(0);

// tab animation
const changeTab = (index) => {
  if (index !== activeTab.value) {
    gsap.to(
      `#feature-detail img, #feature-detail h1, #feature-detail p, #feature-detail button`,
      {
        opacity: 0,
        x: 70,
        duration: 0.3,
        ease: "power2.inOut",
        onComplete: () => {
          activeTab.value = index;
          gsap.fromTo(
            `#feature-detail img, #feature-detail h1, #feature-detail p, #feature-detail button`,
            { opacity: 0, x: 70 },
            { opacity: 1, x: 0, duration: 0.3, ease: "power2.inOut" }
          );
        },
      }
    );
  }
};

onMounted(() => {
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: "#tab",
      start: "top center",
      end: "bottom center",
      scrub: 1,
      once: true,
    },
  });

  tl.from("#tab", {
    opacity: 0,
    y: 50,
    ease: "slow",
    duration: 3,
  }).from("#feature-detail", {
    opacity: 0,
    y: 50,
    ease: "slow",
    duration: 3,
  });
});
</script>
