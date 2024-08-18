<template>
  <div class="container mx-auto px-5 py-20">
    <div class="text-center max-w-md mx-auto">
      <h2
        id="contact-subtitle"
        class="text-xs text-white tracking-[0.6em] mb-4"
      >
        {{ details.subTitle }}
      </h2>
      <h1
        id="contact-title"
        class="text-2xl md:text-3xl text-white font-semibold mb-7"
      >
        {{ details.title }}
      </h1>
    </div>
    <div
      class="flex-col input-form flex max-w-md lg:max-w-lg md:flex-row mx-auto items-center gap-4 justify-center"
    >
      <div class="w-full">
        <input
          v-model="email"
          @input="validateEmail"
          type="email"
          placeholder="Enter your email address"
          class="bg-white p-3 px-4 text-vdBlue w-full focus:outline-none rounded"
        />
        <p
          v-if="emailError"
          class="text-softRed tracking-wide md:absolute text-sm mt-2"
        >
          Whoops! Make sure it's a valid email.
        </p>
      </div>
      <button
        class="bg-softRed rounded hover:text-softRed border-softRed border hover:bg-white duration-300 ease-in-out text-white w-full md:w-[40%] p-3 focus:outline-none"
      >
        {{ details.contactButton }}
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

const email = ref("");
const emailError = ref(false);

const validateEmail = () => {
  const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  emailError.value = !emailPattern.test(email.value);
};

onMounted(() => {
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: "#contact-title",
      start: "bottom bottom",
      end: "bottom bottom",
      scrub: 1,
      once: true,
    },
  });

  tl.from("#contact-subtitle", {
    opacity: 0,
    y: 50,
    ease: "slow",
    duration: 3,
  });

  tl.from("#contact-title", {
    opacity: 0,
    y: 50,
    ease: "slow",
    duration: 3,
  });

  tl.from(".input-form", {
    opacity: 0,
    y: -50,
    ease: "slow",
    duration: 3,
  });
});
</script>
