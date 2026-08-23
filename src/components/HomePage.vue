<template>
<header>

</header>
    <!-- Background  -->
    <div class="grid-background-2">

    <!-- Header -->
    <div class="flex flex-row justify-between space gap-10"> 
        <!-- About me image and bio -->
        <div class="flex flex-wrap p-5">
            <img class="w-50 h-70" :src="Me"></img>
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
            <div class="text base text-brand-primary pt-2 pb-3">Links</div>
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
                :repository="project.repository"
            >
              <p>
                This project simulates gravitational interactions between bodies to model cosmic evolution in Rust. 
                By utilizing the <span class="text-brand-primary">Barnes-Hut algorithm</span>, the computational complexity of this project drops from O(n²) to O(n log n). 
                Hundreds of thousands of bodies can be simulated in realtime to visualize the evolution of cosmic bodies. By utilizing <span class="text-brand-primary">Rust and WebGPU</span>, the calculations for the simulation are be parallelized allowing for multi-million body simulations. 
                Coloring algorithms allow for data-oriented visualizations. This project was originally implemented in <span class="text-brand-primary">Julia</span> as a proof of concept, later it was switched to Rust for a performant and compact implementation.
              </p> 
            </ProjectCard>

            <label class="text-2xl">Work Experience</label> 
            <WorkCard
                v-for="work in workExperience"
                :key="work.title"
                :image-src="XYPROLogo"
                :technologies="work.technologies"
                :title="work.title"
                :highlights="work.highlights"
                :start-date="work.startDate"
                :end-date="work.endDate"
            >
            <p>
                At XYPRO, I led the development effort for the migration of SQLXPress, an interface for the SQL subsystem on the HPe Nonstop, from a legacy Delphi client and C99 server exceeding 1M LOC to a modern stack built on Rust, Vue, and Java. I worked closely with architects to outline key SQL features and their implementations, often providing insight into requirements and concerns for implementations. As a full-stack developer, I worked across the Tauri-based client through to the Spring Boot backend. I held regular code reviews with developers and automation engineers to ensure code quality. I ran our scrum meetings, led sprint planning, and onboarded new interns into the teams stack and processes. By utilizing Tauri and Vue, our new client showed large performance gains and provided a more modern look.
            </p>
            </WorkCard>
        </div>
    </div>

    </div>
</template>


<script setup lang="ts">
import ProjectCard from './ProjectCard.vue';
import Me from '../assets/me_2.jpeg';
import SimulationGif from '../assets/barneshut_no_watermark.gif';
import XYPROLogo from '../assets/xypro.png';
import WorkCard from './WorkCard.vue';

interface Link {
    url: string,
    title: string
}

interface Project {
    title: string;
    technologies: string[];
    highlights: string[];
    imageSrc: string;
    repository: string;
}

interface Work {
    title: string;
    technologies: string[];
    highlights: string[];
    imageSrc?: string;
    startDate: string;
    endDate: string;
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
        title: "Barnes-Hut Simulation",
        technologies: ["Julia","Rust", "WebGPU"],
        highlights: [
            "Simulated the gravitational pull and evolution of millions of particles in Rust.",
            "Implemented a bounding volume hierarchy data structure with the Barnes-Hut algorithm to accelerate simulation speed.",
            "Wrote a WebGPU shader to leverage GPU processing to greatly speedup computation time.",
            "Developed an file format for exporting the current state of the simulation, allowing for pausing and resuming simulations."
        ],
        imageSrc: SimulationGif,
        repository: "https://github.com/MaxTheMighty/BarnesHutSimulation",

    },

]

const workExperience: Work[] = [{
    title: "Engineer I - Software",
    technologies: ["Rust","Vue","Tauri","Typescript","Delphi","Java","Springboot","SQL"],
    highlights: [
        "Led the migration of a 1M+ LOC legacy DBMS client from Delphi/C99 to a modern Rust, Vue, and Java stack",
        "Delivered significant performance and responsiveness by rebuilding the client on Tauri and Rust",
        "Architected and modernized both the front-end and back-end of our large DBMS client",
        "Maintained our legacy Delphi-based client, providing bugfixes and new SQL feature support",
        "Developed a Tauri-based client for HPe Nonstop specific keystore functionality from the ground up",
        "Contributed to migration planning and provided feature demos to stakeholders",
        "Enforced code quality and security standards through Rust code reviews",
        "Acted as a subject matter expert for HPe Nonstop subsystems"],
    startDate: "January 2024",
    endDate: "Present"

}]
</script>