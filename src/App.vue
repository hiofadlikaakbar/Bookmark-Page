<template>
  <Header />
  <section role="region">
    <Hero :details="heroAssets" />
  </section>
  <section role="region">
    <Features :details="featureAssets" />
  </section>
  <section role="region">
    <Extension :details="extensionAssets" />
  </section>
  <section role="region">
    <Faq :details="faqPage"></Faq>
  </section>
  <section role="region" class="bg-softBlue">
    <Contact :details="contactDetails" />
  </section>
  <footer role="contentinfo" class="bg-vdBlue">
    <Footer :details="footerDetails" />
  </footer>
</template>

<script setup>
// component vue
import Header from "./components/Header.vue";
import Hero from "./components/Hero.vue";
import Features from "./components/Features.vue";
import Extension from "./components/Extension.vue";
import Faq from "./components/Faq.vue";
import Contact from "./components/Contact.vue";
import Footer from "./components/Footer.vue";

// assets images
import heroImage from "./assets/illustration-hero.svg";
import simpleBookmarking from "./assets/illustration-features-tab-1.svg";
import speedySearching from "./assets/illustration-features-tab-2.svg";
import easySharing from "./assets/illustration-features-tab-3.svg";
import chrome from "./assets/logo-chrome.svg";
import firefox from "./assets/logo-firefox.svg";
import opera from "./assets/logo-opera.svg";
import dot from "./assets/bg-dots.svg";
import logo from "./assets/footer-logo.svg";
import fb from "./assets/icon-facebook.svg";
import twt from "./assets/icon-twitter.svg";
const heroAssets = {
  src: heroImage,
  alt: "Hero images",
  heroTitle: "A Simple Bookmark Manager",
  buttonChrome: "Get it on Chrome",
  buttonFirefox: "Get it on Firefox",
};

const featureAssets = {
  featureTitle: "Features",
  featureDesc:
    "Our aim is to make it quick and easy for you to access your favorite websites. Your bookmarks sync between your devices and browsers, so you can access them anywhere you wish.",
  features: [
    {
      src: simpleBookmarking,
      alt: "Simple Bookmarking",
      title: "Bookmark in one click",
      desc: "Organize your bookmarks however you like. Our simple drag-and-drop interface gives you complete control over how you manage your favourite sites.",
    },
    {
      src: speedySearching,
      alt: "Speedy Searching",
      title: "Intelligent Search",
      desc: "Our powerful search feature will help you find saved sites in no time at all. No need to trawl through all of your bookmarks.",
    },
    {
      src: easySharing,
      alt: "Easy Sharing",
      title: "Share your bookmarks",
      desc: "Easily share your bookmarks and collections with others. Create a shareable link that you can send at the click of a button.",
    },
  ],
  buttonInfo: "More Info",
};

const extensionAssets = {
  extensionTitle: "Download the extension",
  extensionDesc:
    "We've got more browsers in the pipeline. Please do let us know if you've got a favorite you'd like us to prioritize.",
  dot: dot,
  dotAlt: "Dot Line",
  browsers: [
    {
      src: chrome,
      title: "Add to Chrome",
      alt: "Chrome Images",
      info: "Minimum version 62",
    },
    {
      src: firefox,
      alt: "Firefox Images",
      title: "Add to Firefox",
      info: "Minimum version 55",
    },
    {
      src: opera,
      alt: "Opera Images",
      title: "Add to Opera",
      info: "Minimum version 46",
    },
  ],
  installButton: "Add & Install Extension",
};

const faqPage = {
  faqTitle: "Frequently Asked Questions",
  faqDesc:
    "Here is some of our FAQs. If you have any other questions you'd like answered please feel free to mail us.",
  faqAccordion: [
    {
      accordionTitle: "What is bookmark",
      accordionDesc:
        "A bookmark is a feature that allows users to save and manage links to web pages they frequently visit or want to remember for later. It is similar to marking a page in a book, making it easy for users to return to that page without having to search for it again.",
    },
    {
      accordionTitle: "How can i request a new browser?",
      accordionDesc:
        "To request a new browser, please contact our IT support team through the support portal or send an email to support@bookmark.com. Include details about why you need the new browser and any specific requirements you have. Our team will review your request and get back to you with further instructions.",
    },
    {
      accordionTitle: "Is there a mobile app?",
      accordionDesc:
        "Yes, we have a mobile app available for both iOS and Android. You can download it from the App Store or Google Play Store. The app provides easy access to all our services on the go.",
    },
    {
      accordionTitle: "What about other Chromium browsers?",
      accordionDesc:
        "Other Chromium browsers, such as Google Chrome, Microsoft Edge, and Opera, are also supported. They offer similar features and compatibility. Feel free to use the one that best suits your needs.",
    },
  ],
  faqButton: "More Info",
};

const contactDetails = {
  subTitle: "35,000+ ALREADY JOINED",
  title: "Stay up-to-date with that we're doing",
  contactButton: "Contact Us",
};

const footerDetails = {
  src: logo,
  alt: "logo",
  fb: fb,
  twt: twt,
  links: [
    { label: "FEATURES", href: "#" },
    { label: "PRICING", href: "#" },
    { label: "CONTACT", href: "#" },
  ],
};
</script>
