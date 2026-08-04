<template>
<header>

</header>
    <!-- Background  -->
    <div class="grid-background-2">

    <!-- Header -->
    <div class="flex flex-row justify-between space gap-10"> 
        <!-- About me image and bio -->
        <div class="flex flex-wrap p-5">
            <img class="w-50 h-70" src="../assets/me.jpg"></img>
            <div class="min-w-0 flex-1">
            <p class="px-3 text-wrap">
                My name is Maxwell and I am a Software Engineer with a passion for simulations and engines. I have professional experience with legacy software as well as modern frameworks, and personal experience with simulations and engines. I focus on 
                writing quality software that is maintainable and delivers a positive user experience.
            </p>
            <!-- <p class="text-orange-600">
                Sample orange text
            </p> -->
        </div> 
        </div>

        <!-- Links -->
        <div class="flex flex-wrap px-3 m-3 bg-white border border-black gap-10">
        <ul class="">
            <div class="text base text-orange-600 pt-2 pb-3">Links</div>
            <li v-for="link in links" class="text hover:text-blue-500">
             <a :href="link.url">{{ link.title }}</a>
            </li>
            </ul>
        </div>
    </div>

    <!-- Main content -->
    <div class="flex flex-col gap-6 px-5 py-3">
        <label class="text-2xl">Personal Projects</label> 

        <div class="flex flex-col gap-4">
            <ProjectCard
                v-for="project in projects"
                :key="project.title"
                :image-src="project.imageSrc"
                :title="project.title"
                :technologies="project.technologies"
                :highlights="project.highlights"
            />
        </div>
    </div>

    </div>
</template>


<script setup lang="ts">
import ProjectCard from './ProjectCard.vue';
import profileImage from '../assets/me.jpg';

interface Link {
    url: string,
    title: string
}

interface Project {
    title: string;
    technologies: string[];
    highlights: string[];
    imageSrc: string;
}

const links: Array<Link> = [
    {
        url: "https://github.com/maxthemighty",
        title: "Github"
    },
    {
        url: "https://www.linkedin.com/in/maxwell-kozlov-a22a851a3/",
        title: "LinkedIn"
    }
]

const projects: Project[] = [
    {
        title: "Simulation Sandbox",
        technologies: ["C++", "OpenGL", "Physics"],
        highlights: [
            "Built a modular renderer and entity system for prototype simulations.",
            "Focused on clean abstractions that made it easy to iterate on scenes quickly."
        ],
        imageSrc: profileImage
    },
    {
        title: "Resume Website",
        technologies: ["Vue", "TypeScript", "Tailwind CSS"],
        highlights: [
            "Created a polished single-page portfolio to showcase experience and projects.",
            "Kept the layout flexible so new sections can be added without redesigning the whole page."
        ],
        imageSrc: profileImage
    }
]

</script>