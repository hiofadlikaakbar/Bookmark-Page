<template>
  <div class="container mx-auto px-5 mt-20 lg:mt-32 pb-32">
    <div id="faq-title" class="text-center mb-16">
      <h1 class="text-vdBlue text-2xl md:text-3xl lg:text-4xl font-medium mb-7">
        {{ details.faqTitle }}
      </h1>
      <p
        class="text-base md:text-lg lg:text-xl lg:max-w-2xl mx-auto text-grayishBlue"
      >
        {{ details.faqDesc }}
      </p>
    </div>
    <!-- accordions -->
    <div
      class="grid grid-cols-1 max-w-2xl cursor-pointer mx-auto"
      id="accordions"
    >
      <div v-for="(item, index) in accordionItems" :key="index">
        <div
          class="p-5 border-t accordion border-b group border-grayishBlue/40"
          v-auto-animate
          @click="toggleAccordion(index)"
        >
          <div
            class="flex items-center justify-between"
            :class="{ 'mb-5': item.show, 'mb-0': !item.show }"
          >
            <div>
              <p
                class="text-vdBlue font-medium group-hover:text-softRed duration-300 ease-in-out tracking-wide md:text-lg text-base"
              >
                {{ item.title }}
              </p>
            </div>
            <i
              class="fa-solid"
              :class="{
                'fa-chevron-down text-lg text-softBlue': !item.show,
                'fa-chevron-up text-lg text-softRed': item.show,
              }"
            ></i>
          </div>
          <p class="text-base md:text-lg text-grayishBlue" v-if="item.show">
            {{ item.content }}
          </p>
        </div>
      </div>
      <button
        class="px-7 button-info mt-16 mx-auto py-3 block hover:text-softBlue border-softBlue border duration-300 ease-in-out hover:bg-white rounded-md bg-softBlue text-white"
      >
        {{ details.faqButton }}
      </button>
    </div>
  </div>
</template>

<script setup>
import gsap from "gsap";
import { ref, onMounted } from "vue";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

const props = defineProps({
  details: {
    type: Object,
    required: true,
  },
});

const accordionItems = ref([
  {
    title: "What is Bookmark",
    content:
      "A bookmark is a feature that allows users to save and manage links to web pages they frequently visit or want to remember for later. It is similar to marking a page in a book, making it easy for users to return to that page without having to search for it again.",
    show: false,
  },
  {
    title: "How can i request a new browser?",
    content:
      "To request a new browser, please contact our IT support team through the support portal or send an email to support@bookmark.com. Include details about why you need the new browser and any specific requirements you have. Our team will review your request and get back to you with further instructions.",
    show: false,
  },
  {
    title: "Is there a mobile app?",
    content:
      "Yes, we have a mobile app available for both iOS and Android. You can download it from the App Store or Google Play Store. The app provides easy access to all our services on the go.",
    show: false,
  },
  {
    title: "What about other Chromium browsers?",
    content:
      "Other Chromium browsers, such as Google Chrome, Microsoft Edge, and Opera, are also supported. They offer similar features and compatibility. Feel free to use the one that best suits your needs.",
    show: false,
  },
]);
const toggleAccordion = (index) => {
  accordionItems.value.forEach((item, i) => {
    item.show = i === index ? !item.show : false;
  });
};

onMounted(() => {
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: "#faq-title",
      start: "top center",
      end: "bottom center",
      scrub: 1,
      once: true,
    },
  });

  tl.from("#faq-title", {
    opacity: 0,
    y: 50,
    ease: "slow",
    duration: 3,
  });
  tl.from("#accordions", {
    opacity: 0,
    y: 50,
    ease: "slow",
    duration: 3,
  });
});
</script>
