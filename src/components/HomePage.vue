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
                My name is Maxwell and I am a Software Engineer with a passion for simulations and engines. I have professional experience with [legacy software sqlxpress stuff] and personal experience with [space simluation stuff]
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
    <div class="flex flex-row justify-between space gap-10">
        <div class="flex flex-wrap px-5 py-3">
           <label class="text-2xl">Personal Projects</label> 

        </div>
    </div>

    </div>
</template>


<script setup lang="ts">

interface Link {
    url: string,
    title: string
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

</script>