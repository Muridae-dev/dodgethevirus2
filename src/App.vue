<template>

  <div class="thumbnail" v-for="(windowedComponent, index) in windowedComponents" :key="index">
    <img :src="require('./assets/icons/' + windowedComponent.thumbnail)" />
  </div>

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
          // COMPONENT INFO
          component: "Terminal",
          thumbnail: "terminal.svg",


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

  .thumbnail {
    height:100px;
    width:100px;
    background:white;
  }
</style>
