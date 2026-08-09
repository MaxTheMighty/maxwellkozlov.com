<template>
    <iframe :src="props.link" >

    </iframe>
</template>

<script setup lang="ts">
interface Props {
    visible: boolean
    link: string
}

const props = defineProps<Props>();
</script>
