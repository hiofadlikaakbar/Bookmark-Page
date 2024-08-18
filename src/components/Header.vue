<template>
  <header class="pb-36">
    <nav id="navbar" class="p-5 bg-white/80 xl:px-16 w-full fixed z-50">
      <div class="flex justify-between mx-auto items-center">
        <div class="flex items-center gap-5">
          <img
            v-if="!isWhiteLogoVisible"
            :src="logo"
            alt="logo"
            class="relative z-50"
          />
          <img v-else :src="whiteLogo" alt="logo" class="relative z-50" />
        </div>
        <div class="flex items-center gap-5">
          <img :src="whiteLogo" alt="logo" class="relative hidden z-50" />
        </div>
        <ul class="hidden lg:flex gap-10 items-center">
          <li v-for="(link, index) in links" :key="index">
            <a
              :href="link.label"
              class="text-vdBlue focus:outline-none hover:text-softRed duration-200 ease-in-out"
              >{{ link.label }}</a
            >
          </li>
          <button
            class="py-2 rounded px-7 bg-softRed focus:outline-none hover:text-softRed border-softRed border hover:bg-white duration-300 ease-in-out text-white"
          >
            LOGIN
          </button>
        </ul>
        <button @click="toggleNav" class="block lg:hidden focus:outline-none">
          <img
            :src="burgerMenu"
            alt="burger"
            ref="burger"
            class="relative z-50"
          />
        </button>
      </div>
      <div class="relative">
        <ul
          :class="showMenu ? 'right-0 grid' : 'right-[-100%] grid opacity-0'"
          class="h-screen w-full fixed duration-500 text-center lg:hidden px-5 ease-in-out content-start pt-24 space-y-7 md:space-y-12 top-0 right-0 bg-vdBlue/95 shadow-xl"
        >
          <li
            v-for="(link, index) in links"
            :key="index"
            class="pb-2 pt-2 xs:pb-4 xs:pt-4 border-b-[1px] border-t-[1px] border-white/20"
          >
            <a
              :href="link.href"
              class="text-white tracking-widest focus:outline-none text-lg md:text-lg mb-12"
              >{{ link.label }}</a
            >
          </li>
          <button
            class="uppercase text-white focus:outline-none font-semibold border-2 px-4 py-3 rounded text-lg tracking-widest border-white"
          >
            login
          </button>
          <div class="flex gap-8 justify-center pt-64 items-center">
            <img :src="fb" alt="facebook" />
            <img :src="tweet" alt="tweeter" />
          </div>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script setup>
import logo from "../assets/logo-bookmark.svg";
import gsap from "gsap";
import whiteLogo from "../assets/logo-bookmark-white.svg";
import burgerMenu from "../assets/icon-hamburger.svg";
import closeMenu from "../assets/icon-close.svg";
import fb from "../assets/icon-facebook.svg";
import tweet from "../assets/icon-twitter.svg";
import { ref, onMounted } from "vue";

const burger = ref(null);
const showMenu = ref(false);
const isWhiteLogoVisible = ref(false);

const toggleNav = () => {
  showMenu.value = !showMenu.value;
  isWhiteLogoVisible.value = !isWhiteLogoVisible.value;
  if (isWhiteLogoVisible.value) {
    burger.value.src = closeMenu;
  } else {
    burger.value.src = burgerMenu;
  }
};

const links = [
  { label: "FEATURES", href: "#" },
  { label: "PRICING", href: "#" },
  { label: "CONTACT", href: "#" },
];

onMounted(() => {
  gsap.from("#navbar", {
    ease: "back",
    duration: 1,
    x: "-120",
    opacity: 0,
  });
});
</script>
