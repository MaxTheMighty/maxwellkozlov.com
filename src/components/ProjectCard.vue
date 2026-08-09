<template>
  <article class="border border-slate-400 bg-white p-5 text-slate-800">
    <div class="grid grid-flow-row grid-rows-2">
      <!-- Image and bullet points -->
      <div class="flex gap-4">
        <img :src="props.imageSrc" class="h-60 w-60" />

        <!-- Div for holding the title and bullet points and stacking them -->
        <div class="flex-col w-full">
          <!-- Div that holds the title and aligns all the items into a row-->
          <div class="flex gap-4 w-full">
            <h3 class="text-lg text-black">{{ props.title }}</h3>
            <h5 class="text-lg text-gray-500 italic tracking-[0.03em]">
              {{ technologiesPretty }}
            </h5>

            <!-- Link -->
            <h5
              class="text-lg underline decoration-dashed ml-auto text-brand-primary italic"
              link
            >
              <a
                :href="props.repository"
                @mouseenter="onLinkEnter"
                @mouseleave="onLinkLeave"
                >Link</a
              >
            </h5>

            <!-- I frame preview -->
            <!-- Github doesn't let you embed its pages in an iframe, so we can't do this yet -->
            <!-- <ProjectPreview :link="props.repository" :visible="showPreview"></ProjectPreview> -->
          </div>

          <!-- Add the bullet points here -->
          <ul class="list-disc list-inside w-full">
            <li v-for="hi in props.highlights">{{ hi }}</li>
          </ul>
        </div>
      </div>
      <!-- Main content -->
      <div class="py-3">
        <slot></slot>
      </div>
    </div>
  </article>
</template>

<script setup lang="ts">
import { ref } from "vue";

interface Props {
  imageSrc: string;
  title: string;
  technologies: string[];
  highlights: string[];
  repository: string;
  content: string;
}

const props = defineProps<Props>();
const technologiesPretty = props.technologies.join(" / ");
const showPreview = ref<boolean>(false);

const onLinkEnter = (e: Event) => {
  showPreview.value = true;
};

const onLinkLeave = (e: Event) => {
  showPreview.value = false;
};
</script>

<style scoped></style>
