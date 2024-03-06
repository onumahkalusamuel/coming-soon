<script setup lang="ts">

import axios, {type AxiosError} from 'axios';
import {notify} from "@kyvg/vue3-notification";
import CountdownComponent from "@/components/CountdownComponent.vue";
import IconEnvelop from "@/components/icons/IconEnvelop.vue";
import TextInputComponent from "@/components/TextInputComponent.vue";
import {ref} from "vue";

const dueDate = new Date("04-20-2024");
const email = ref('');
const emailRegex: RegExp = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

const submitForm = async (e: Event) => {
  e.preventDefault();
  if (!emailRegex.test(email.value)) {
    notify({type: 'error', text: "Please enter a valid email address."})
    return;
  }
  const form = {email: email.value, website: window.location.hostname}

  try {
    const response = await axios.post('/submit.php', form);
    if (response.status >= 200 && response.status < 300) {
      notify({type: 'success', text: "Your email has been received. We will keep you in the loop.", duration: 5000});
    } else {
      notify({type: 'error', text: response.data.message || "An error occurred. Please try again later."});
    }
  } catch (error) {
    console.error('Error submitting form:', error);
    notify({
      type: 'error',
      text: ((error as unknown as AxiosError)?.response?.data as { message: string })?.message
          || "An error occurred. Please try again later."
    });
  }
}

</script>

<template>
  <main
      class="px-5 pb-10 md:px-16 mx-auto w-full max-w-[1200px] flex-1 flex flex-wrap bg-no-repeat bg-contain bg-right-top md:bg-saly"
  >
    <div class="md:w-[460px] pe-16 pt-10 flex items-center">
      <div>
        <div class="text-[#BC457F] font-semibold text-sm py-3">COMING SOON</div>
        <div class="text-3xl md:text-4xl font-semibold">Exciting website launch coming soon!</div>
        <CountdownComponent :due-date="dueDate"/>
      </div>
    </div>
    <div class="flex flex-col justify-center flex-1 ">
      <div class="md:flex-1"></div>
      <div class="flex md:justify-end md:px-10 md:my-5">
        <div class="drop-shadow-2xl p-5 bg-white w-full">
          <div class="text-lg mb-3">Get notified when we launch</div>
          <div class="mb-2">
            <form method="post" class="flex gap-x-2" @submit="submitForm">
              <TextInputComponent class="flex-1" :prepend="IconEnvelop" type="email" v-model="email" required
                                  placeholder="john.doe@gmail.com"/>
              <button class="bg-[#9F1B86] px-5 h-10 text-white text-sm" type="submit">Notify&nbsp;me</button>
            </form>
          </div>
          <small>*Don't worry we will not spam you 😀 </small>
        </div>
      </div>
    </div>
  </main>
</template>
