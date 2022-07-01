<template>
  <div class="window-container" v-for="windowedComponent in windowedComponents" :key="windowedComponent.component">
    <NewWindow v-if="windowedComponent.isActive" :windowedComponent="windowedComponent">
      <component :is="windowedComponent.component">
      </component>
    </NewWindow>
  </div>
</template>

<script>
import NewWindow from "./components/NewWindow.vue"
import Terminal from "./views/Terminal.vue"

export default {
  name: 'App',
  components: {
    NewWindow,
    Terminal,
  },
  data() {
    return {
      windowedComponents: [
        {
          // COMPONENT NAME
          component: "Terminal",

          // CSS VALUES
          top:"30vh",
          left:"60vw",
          height:"50vh",
          width:"50vw",

          // BOOLEANS
          isActive: true,
          browser: false,


        }
      ]
    }
  }
}
</script>

<style>
  @font-face {
      font-family: "cascadiaCode";
      src: url("./fonts/CascadiaCode.ttf");
  }

  html, body {
    padding:0;
    margin:0;
  }

  body {
    background:black;
  }
</style>
