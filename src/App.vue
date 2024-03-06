<script setup lang="ts">
import {RouterView} from 'vue-router';
import {Notifications} from "@kyvg/vue3-notification";
// import IconLogo from "@/components/icons/IconLogo.vue";
// import IconFacebook from "@/components/icons/IconFacebook.vue";
// import IconYoutube from "@/components/icons/IconYoutube.vue";
// import IconTwitter from "@/components/icons/IconTwitter.vue";
// import IconInstagram from "@/components/icons/IconInstagram.vue";

// const socials = [
//   {title: 'Facebook', icon: IconFacebook},
//   {title: 'YouTube', icon: IconYoutube},
//   {title: 'Twitter', icon: IconTwitter},
//   {title: 'Instagram', icon: IconInstagram}
// ];
</script>

<template>
  <div class="flex flex-col w-full min-h-screen">
<!--    <header class="px-5 md:px-16 m-auto w-full py-5 max-w-[1200px]">-->
<!--      <div class="flex items-center justify-between">-->
<!--        <RouterLink to="/">-->
<!--          <div class=" pr-5">-->
<!--          <IconLogo></IconLogo>-->
<!--          </div>-->
<!--        </RouterLink>-->
<!--        <div class="flex gap-x-2">-->
<!--          <div v-for="(social, i) in socials" :key="i" class="bg-[#F5F7FA] rounded-sm p-3">-->
<!--            <component :is="social.icon"/>-->
<!--          </div>-->
<!--        </div>-->
<!--      </div>-->
<!--    </header>-->
    <RouterView/>
    <notifications />
    <footer class="p-5 md:px-16 m-auto w-full py-5 max-w-[1200px] text-sm flex items-center justify-between flex-wrap">
      <div class="flex space-x-1 flex-wrap pb-3">
        <div>&copy; 2024 - Site by Zebitech.</div>
        <div>All rights reserved.</div>
      </div>
      <div class="flex gap-x-3 pb-3">
        <a href="#">FAQs</a>
        <a href="#">Privacy Policy</a>
        <a href="#">Terms &amp; Condition</a>
      </div>
    </footer>
  </div>
</template>
