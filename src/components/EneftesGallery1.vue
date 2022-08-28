<template>
    <div class="gallery1-container">
        <div class="gallery1-arrow" style="left:0;" @click="currentImage > 0 ? currentImage-- : null"></div>
        <div class="gallery1-pic" v-for="(image, index) in images" :key="image.src" :style="{left: `calc(50% + ${(index + (currentImage*-1))*500}px)`}">
            <img :src="image.src" />
        </div>
        <div class="gallery1-arrow" style="right:0;" @click="currentImage < images.length-1 ? currentImage++ : null"></div>
    </div>
</template>

<script>
export default {
    name: "EneftesGallery1",
    props: ["folderLink"],
    data() {
        return {
            images: [],
            currentImage: 0,
        }
    },
    async created() {

        if(this.folderLink){
            this.images = await this.importAll(require.context(`../assets/hempfarm/images/AI-Images/`, false, /\.(png|jpe?g|svg)$/))
            console.log(this.folderLink)
        }
    },
    methods: {
        importAll(r) {
            let imagesTemp = {}
            r.keys().forEach((item, index) => {
                imagesTemp[item.replace('./', '')] = r(item);
            });
            let imagesArray = Object.keys(imagesTemp).map(image => {let img = new Image(); img.src = require('../assets/hempfarm/images/AI-Images/' + image); return img;})
            console.log(imagesArray)
            return imagesArray
            
        },
        testing() {
            console.log(this.images)
        }
    }
}
</script>

<style lang="scss" scoped>
    .gallery1-container {
        height:400px;
        width:100%;
        text-align:center;
        position:relative;

        

        .gallery1-arrow {
            width:50px;
            height:400px;
            background:rgba(0, 0, 0, 0.5);
            z-index:1;
            position:absolute;

        }

        .gallery1-pic {
            position:absolute;
            top:0;
            transform:translateX(-50%);
            z-index: 0;
            transform-style: preserve-3d;
            transition:left 1s;
            transition-timing-function:ease;
        }

        img {
            width:400px;
            height:auto;
            
        }
    }
</style>
