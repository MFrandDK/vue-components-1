<template>
    <img :src="`./assets/${imgSrc}`" alt="">
</template>



<script>
export default {
    name: "ToyImage",
    props: {
        imgSrc: String,
    },
};
</script>



<style scoped>
img {
    width: 200px;
    border: 2px solid black;
    padding: 5px;
    border-radius: 6px;
}
</style>