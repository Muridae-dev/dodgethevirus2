<template>
  <div class="main-container">
    <div class="thumbnail-for" v-for="(windowedComponent, index) in windowedComponents" :key="index">
      <Thumbnail :windowedComponent="windowedComponent" :index="index" />
    </div>

    <div class="window-container" v-for="windowedComponent in windowedComponents" :key="windowedComponent.component">
      <NewWindow v-if="windowedComponent.isActive" :windowedComponent="windowedComponent">
        <component :is="windowedComponent.component">
        </component>
      </NewWindow>
    </div>
  </div>
</template>

<script>
import NewWindow from "./components/NewWindow.vue"
import Thumbnail from "./components/Thumbnail.vue"

import Terminal from "./views/Terminal.vue"
import Biggie from "./views/Biggie.vue"
import Murky from "./views/Murkys.vue"
import Unknown from "./views/Unknown.vue"
import KahunaBurger from "./views/KahunaBurger.vue"

export default {
  name: 'App',
  components: {
    NewWindow,
    Terminal,
    Thumbnail,
    Biggie,
    Murky,
    Unknown,
    KahunaBurger
  },
  data() {
    return {
      player: [
        {
          name: "",
          health: "",
          virus: "",
          money: 0,
        }
      ],
      windowedComponents: [
        {
          // COMPONENT INFO
          component: "Terminal",
          name: "Terminal",

          // THUMBNAIL
          imgSrc: "thumbnails/terminal.png",

          // CSS VALUES
          top:"30vh",
          left:"60vw",
          height:"50vh",
          width:"50vw",

          // BOOLEANS
          isActive: false,
          browser: false,
        },

        {
          // COMPONENT NAME
          component: "Biggie",
          name: "Biggie INC",

          // THUMBNAIL
          imgSrc: "mascots/biggie.png",

          // CSS VALUES
          top:"50vh",
          left:"50vw",
          height:"80vh",
          width:"80vw",

          // BOOLEANS
          isActive: false,
          browser: true,
        },

        {
          // COMPONENT NAME
          component: "Murky",
          name: "Murkys raft",

          // THUMBNAIL
          imgSrc: "mascots/murky.png",

          // CSS VALUES
          top:"50vh",
          left:"50vw",
          height:"80vh",
          width:"80vw",

          // BOOLEANS
          isActive: false,
          browser: true,
        },

        {
          // COMPONENT NAME
          component: "Unknown",
          name: "Test",

          // THUMBNAIL
          imgSrc: "mascots/occult2.png",

          // CSS VALUES
          top:"50vh",
          left:"50vw",
          height:"80vh",
          width:"80vw",

          // BOOLEANS
          isActive: false,
          browser: true,
        },

        {
          // COMPONENT NAME
          component: "KahunaBurger",
          name: "Big Kahuna Burger",

          // THUMBNAIL
          imgSrc: "thumbnails/samLjackson.jpeg",

          // CSS VALUES
          top:"50vh",
          left:"50vw",
          height:"90vh",
          width:"90vw",

          // BOOLEANS
          isActive: false,
          browser: true,
        },

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
    z-index:0;
    background:black;
    color:white;
  }

  .main-container {
    height:100vh;
    width:100vw;
  }

  .thumbnail-for {
    z-index:1;
  }

  .thumbnail {
    height:100px;
    width:100px;
    background:white;
  }
</style>
