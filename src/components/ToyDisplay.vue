<template>
    <div>
        <h2>{{toy.name}}</h2>
        <ToyImage :imgSrc="toy.url"></ToyImage>
        <p>{{toy.description}}</p>
    </div>
</template>

<script>
import ToyImage from './ToyImage.vue';


export default {
    name: "ToyDisplay",
    props: {
        toy: {
            type: Object,
            required: true,
        },
    },
    components: { ToyImage }
}
</script>

<style scoped>
</style>