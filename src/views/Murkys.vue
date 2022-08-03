<template>
    <section class="murky-container">
        <div class="murky-background-container" v-for="(background, index) in backgrounds" :key="index">
            <img :src="background.src" class="murky-background-image" :style="{'z-index': index}"/>
        </div>

        <StaticBackground staticProfile="Murky"/>

        <div class="murky-main-title">
            MURKYS <br/>RAFT
        </div>
        <article>
            Global leader in distribution of fish
        </article>
    </section>
</template>

<script>
import StaticBackground from "../components/StaticBackground.vue"

export default {
    components: {
        StaticBackground,
    },
    data() {
        return {
            backgrounds: [],
        }
    },
    async created() {
        this.backgrounds = await this.importAll(require.context('../assets/murky/backgrounds', false, /\.(png|jpe?g|svg)$/))
    },
    methods: {
        importAll(r) {
            let backgroundsTemp = {}
            r.keys().forEach((background) => {
                backgroundsTemp[background.replace('./', '')] = r(background);
            });
            let backgroundsArray = Object.keys(backgroundsTemp).map(background => {let img = new Image(); img.src = require('../assets/murky/backgrounds/' + background); return img;})

            return backgroundsArray
        },
    }
}
</script>

<style scoped>
    .murky-container {
        height:calc(100% - 72px);
        width:100%;
        position:relative;
        font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
        overflow-y:hidden;
        

    }

    .murky-main-title {
        position:absolute;
        left:10px;
        font-size:10em;
        line-height:0.9em;
        z-index:1;
        
    }

    .murky-background-container {
        position:absolute;
        top:0;
        left:0;
        width:100%;
        height:100%;
        z-index:-1;
    }

    .murky-background-image {
        position:absolute;
        height:auto;
        width:100%;
    }

    article {
        position:absolute;
        bottom:10px;
        left:10px;
    }
</style>