<template>
    <div class="biggie-container">
        <img :src="require('../assets/biggie/biggieBackground.jpeg')" class="background-image" alt="background image"/>

        <div class="biggie-face">
            <img src="../assets/mascots/biggie.png" />
        </div>

        <div class="song-container" v-for="(songArray, index) in songsArray" :key="index" 
        :style="{top: songArray.top, left: songArray.left}"
        @click="playSong(songArray.songSrc)">
            {{songArray.text}}
        </div>
    </div>
</template>

<script>
export default {
    name: "Biggie",
    data() {
        return {
            song: "",
            songsArray: [
                {
                    text: "1970 SOMETHING",
                    songSrc: "1970somethin.mp3",
                    top: "50%",
                    left: "25%",
                },
                {
                    text: "GIMME THE LOOT",
                    songSrc: "gimmetheloot.mp3",
                    top: "10%",
                    left: "50%",
                },
                {
                    text: "HYPNOTIZE",
                    songSrc: "hypnotize.mp3",
                    top: "90%",
                    left: "50%",
                },
                {
                    text: "JUICY",
                    songSrc: "juicy.mp3",
                    top: "50%",
                    left: "75%",
                },

            ]
        }
    },
    methods: {
        playSong(songSrc) {
            this.song = new Audio(require(`../assets/biggie/${songSrc}`));
            this.song.play();
        }
    },
}
</script>

<style>
    .biggie-container {
        height:calc(100% - 72px);
        width:100%;
        position:relative;
    }

    .biggie-face {
        height:50%;
        width:auto;
        position:absolute;
        left:50%;
        top:50%;

        transform:translate(-50%,-50%);
    }
    
    .song-container {
        position:absolute;
        transform:translate(-50%,-50%);
        width:100px;
        height:50px;
        background:blue;
        text-align:center;

    }
</style>

<style scoped>
    .background-image {
        width:100%;
        height:100%;
        position:absolute;
    }

    img {
        height:100%;
        width:auto;
    }
</style>