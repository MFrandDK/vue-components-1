<!-- In this app we will try and implement a few child components and learn to pass props. Have a look at this diagram to get a sence of the flow of data: https://mmd.ucn.dk/lecturer/mfw/assets/img/VueComp1.png and a link of a finished version: https://mmd.ucn.dk/lecturer/mfw/vue-apps/vue-components-1/ -->

<!-- Short version -->
<!-- 1. Import toys and create a button for each that, when clicked, updates a value that keeps track of what toy we want to see (selectedToyId) -->
<!-- 2. Make a method called getSelectedToy that returns the toy (object) with the selectedToyId -->
<!-- 3. Make a child component called ToyDisplay that will render the selected toy - so you have to pass it props -->
<!-- 4. Make a new component - <ToyImage> that you will use to render images. It needs the url for the images as a prop and the name (for the alt-attribute) as a prop. -->
<!-- 5. Style it with scoped styling and make it look and act like the finished version above -->
<!-- Extra assignment: upload it to your mmd studentserver in a new folder and send the link to your teacher -->
<!-- Extra assignment: figure out how to implement a method that triggers when you click the img in "ToyDisplay", that will make App.vue console.log("My child component has been clicked!"). So you need an event from a childcomponent to trigger another event on the parent component. You will probably have to google this :) -->

<!-- Longer version -->
<!-- 1. Import "toys" from /assets/toys.js and store in reactive data -->
<!-- 2. Loop throught toys and create a <button> for each with the toys name inside -->
<!-- 3. When you press a button, you should update a reactive value called selectedToyId -->
<!-- 4. We need to get a hold of the actual object from the array "toys". Use a method (getSelectedToy) that returns the selected toy with the selectedToyId -->
<!-- 5. In the folder "components", create a new file: ToyDisplay.vue -->
<!-- 6. Import, register and use ToyDisplay.vue in App.vue -->
<!-- 7. We need to send the data from getSelectedToy to be passed to the childcomponent ToyDisplay as a prop -->
<!-- 8. Create a new childcomponent: ToyImage.vue´in the components folder -->
<!-- 9. Import, register and use the ToyImage component in ToyDisplay to show the images. So you will need to pass the src and alt text to the ToyImage component from the ToyDisplay component -->
<!-- 10. Finally style the component like it is in the above example -->
<!-- Extra assignment: upload it to your mmd studentserver in a new folder and send the link to your teacher -->

<template>
  
  <div class="buttons">
    <button v-for="toy in toys" :key="toy.id" @click="selectedToyId = toy.id">
      {{ toy.name }}
    </button>
  </div>
  <div class="SelectedToy" v-if="selectedToyId">
    <ToyDisplay :toy="getSelectedToy"></ToyDisplay>
  </div>
</template>

<script>
import toys from "@/assets/toys"
import ToyDisplay from "./components/ToyDisplay.vue";

export default {
    name: "App",
    components: {
      ToyDisplay,
    },
    data() {
        return {
            toys,
            selectedToyId: undefined
        };
    },
    computed: {
        getSelectedToy() {
            return this.toys.find(toy => toy.id === this.selectedToyId);
        }
    },
    
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
