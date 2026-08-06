<template>
  <article class="border border-slate-400 bg-white p-5 text-slate-800">
    <div class="grid grid-flow-row grid-rows-2">
      <!-- Image and bullet points -->
      <div class="flex gap-4">
        <img src="../assets/me.jpg" class="h-40 w-40" />

        <!-- Div for holding the title and bullet points and stacking them -->
        <div class="flex-col w-full">

          <!-- Div that holds the title and aligns all the items into a row-->
          <div class="flex gap-4 w-full">
            <!-- Make it so all the text is one row -->
            <h3 class="text-lg text-black">{{ props.title }}</h3>
            <h5 class="text-lg text-gray-500 italic tracking-[0.03em]">
              {{ technologiesPretty }}
            </h5>

            <!-- Link -->
            <h5 class="text-lg underline decoration-dashed ml-auto text-blue-500 italic" link>
              <a :href="props.repository">Link</a>
            </h5>
          </div>

          <!-- Add the bullet points here -->
          <ul class="list-disc list-inside w-full">
            <li v-for="hi in props.highlights">{{ hi }}</li>
          </ul>
        </div>
      </div>
      <!-- Main content -->
      <p class="py-3"> {{ props.content }}</p>
    </div>
  </article>
</template>

<script setup lang="ts">
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
</script>
