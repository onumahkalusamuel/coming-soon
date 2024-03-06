<script setup lang="ts">
import type {Component} from "vue";

defineProps<{
  prepend: Component;
  containerClassName?: string;
  inputClassName?: string;
  type: string | 'text';
  required?: boolean;
  placeholder?: string;
}>()

const model = defineModel();

</script>

<template>
  <div :class="containerClassName">
    <div class="relative">
      <div v-if="prepend" class="absolute px-3 flex items-center h-full">
        <button class="text-lg" type="button">
          <component :is="prepend"/>
        </button>
      </div>
      <input
          v-model="model"
          :required="required"
          :class="inputClassName + ' w-full border-[1px] border-[#091E4224] px-3 h-10 hover:bg-stone-50 focus:outline-none '+ (prepend ? ' pl-10 ' : '')"
          :type="type"
          :placeholder="placeholder"
      />
    </div>
  </div>
</template>