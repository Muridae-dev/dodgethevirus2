<template>
  <div class="main-container">
    <div class="video-container">
      <!--<video muted preload="metadata" autoplay="true">
        <source :src="require(`./assets/videos/VHSTape.mp4`)" type="video/mp4">
      </video>-->
    </div>

    <div class="thumbnail-for" v-for="(windowedComponent, index) in windowedComponents" :key="index">
      <Thumbnail :windowedComponent="windowedComponent" :index="index" />
    </div>

    <div class="window-container" v-for="windowedComponent in windowedComponents" :key="windowedComponent.component">
      <NewWindow v-if="windowedComponent.isActive" :windowedComponent="windowedComponent">
        <component :is="windowedComponent.component" :updateInventory="updateInventory">
        </component>
      </NewWindow>
    </div>
  </div>
</template>

<script>
/* 
  GENERAL CONCEPTS:
    - Final boss battle
      You will have to use the items/party members you have assembled to beat the final boss

      Party members include:
        - Fish (murky)

      Buffs include:
        - Phat tunes (Biggie)
        - Burgers (Big Kahuna Burger)

    
    - Mini-games to make money
      These could be:
        - Blackjack
        - Space invaders
        - Type words fast
*/
import NewWindow from "./components/NewWindow.vue"
import Thumbnail from "./components/Thumbnail.vue"

import Terminal from "./views/Terminal.vue"
import Biggie from "./assets/biggie/Biggie.vue"
import Murky from "./assets/murky/Murkys.vue"
import Unknown from "./views/Unknown.vue"
import KahunaBurger from "./assets/kahuna/KahunaBurger.vue"
import HempFarm from "./assets/hempfarm/HempFarm.vue"

export default {
  name: 'App',
  components: {
    NewWindow,
    Terminal,
    Thumbnail,
    Biggie,
    Murky,
    Unknown,
    KahunaBurger,
    HempFarm
  },
  data() {
    return {
      inventory: [],
      player: [
        {
          name: "",
          health: 10,
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

        {
          // COMPONENT NAME
          component: "HempFarm",
          name: "Hemp Farm",

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
        }

      ]
    }
  },
}
</script>

<style>
  @font-face {
    font-family: "cascadiaCode";
    src: url("./fonts/CascadiaCode.ttf");
  }

  @font-face {
    font-family: "oneUp";
    src: url("./fonts/1up.ttf");
  }

  @font-face {
    font-family: "Isometric";
    src: url("./fonts/3DIsometric-Regular.ttf");
  }

  @font-face {    
    font-family: "Agero";
    src: url("./fonts/agero.ttf");
  }

  @font-face {
    font-family: "AldoApache";
    src: url("./fonts/AldotheApache.ttf");
  }

  @font-face {
    font-family: "Blackout";
    src: url("./fonts/BLACKOUT.TTF");

  }

  @font-face {
    font-family: "Boneapa";
    src: url("./fonts/BONEAPA.TTF");
  }

  @font-face {
    font-family: "Dagestan";
    src: url("./fonts/Dagestan.ttf");
  }

  @font-face {
    font-family: "FippsRegular";
    src: url("./fonts/Fipps-Regular.otf");
  }

  @font-face {
    font-family: "kaOne";
    src: url("./fonts/ka1.ttf");
  }

  @font-face {
    font-family: "Square";
    src: url("./fonts/Square.ttf");
  }

  @font-face {
    font-family: "Squareo";
    src: url("./fonts/Squareo.ttf");
  }

  @font-face {
    font-family: "SuperMario";
    src: url("./fonts/SuperMario256.ttf");
  }

  @font-face {
    font-family:"RobotoBlack";
    src: url("./fonts/Roboto-Black.ttf");
  }

  @font-face {
    font-family:"RussoOne";
    src: url("./fonts/RussoOne-Regular.ttf");
  }

  @font-face {
    font-family:"Ubuntu";
    src: url("./fonts/Ubuntu-Regular.ttf");
  }

  @font-face {
    font-family:"BreeSerif";
    src: url("./fonts/BreeSerif-Regular.ttf");
  }
</style>

<style lang="scss">
  html, body {
    padding:0;
    margin:0;
  }

  body {
    z-index:0;
    background:black;
    color:white;
    font-family:Dagestan;
  }

  body::-webkit-scrollbar-track
  {
      -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
      background-color: black;
  }

  body::-webkit-scrollbar
  {
      width: 10px;
      background-color: black;
  }

  body::-webkit-scrollbar-thumb
  {
      background-color: rgb(4, 255, 150);
      border: 2px solid rgb(4, 255, 150);
  }


  .main-container {
    height:100vh;
    width:100vw;
    position:relative;
  }

  .video-container {
    height:100%;
    width:100%;
    position:absolute;
    top:0;
    left:0;
    overflow:hidden;
    opacity:0.2;

    video {
      position:absolute;
      height:auto;
      width:100%;
      top:50%;
      left:50%;
      transform:translate(-50%,-50%);
    }
  }

  .thumbnail-for {
    z-index:1;
    font-family:Dagestan;
  }

  .thumbnail {
    height:100px;
    width:100px;
    background:white;
  }
  
</style>
