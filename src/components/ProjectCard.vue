<template>
  <article class="border border-slate-400 bg-white p-5 text-slate-800">
    <div class="grid grid-flow-row grid-rows-2">
      <!-- Image and bullet points -->
      <div class="flex justify-start gap-4">
        <img src="../assets/me.jpg" class="h-40 w-40" />
        <h3 class="text-lg text-black">{{ props.title }}</h3>
        <h5 class="text-lg text-gray-500 italic tracking-[0.03em]">
          {{ technologiesPretty }}
        </h5>
      </div>

      <!-- Main content -->
       <p> Blah blah blah, lots of cool tech, blah blah blah</p>
    </div>
  </article>
</template>

<script setup lang="ts">
interface Props {
  imageSrc: string;
  title: string;
  technologies: string[];
  highlights: string[];
}

const props = defineProps<Props>();
const technologiesPretty = props.technologies.join(" / ");
</script>
