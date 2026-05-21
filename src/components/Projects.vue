<template>
    <section class="pb-5" id="projects">
        <h1 class="mt-5 mb-5 pb-4 text-center">My Projects</h1>
        <div v-for="(group, index) in chunkedProjects" :key="index" class="card-deck my-5 justify-content-center">
            <ProjectCard v-for="project in group" :key="project.id" :project="project"/>
        </div>
    </section>
</template>

<script setup>
    import ProjectCard from './ProjectCard.vue';
    import {computed} from 'vue';
    import projects from '../data/projects.json'

    const chunkSize = 3;

    // This function is responsible for splitting the projects array into smaller arrays (chunks)
    const chunkedProjects = computed(() => {
        const chunks = [];

        for(let i=0; i < projects.length; i += chunkSize){
            chunks.push(projects.splice(i, i + chunkSize));
        }
        return chunks;
    })
</script>