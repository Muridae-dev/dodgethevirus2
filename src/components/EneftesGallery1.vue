<template>
    <div class="gallery1-container">
        <div class="gallery1-arrow" style="left:0;" @click="currentImage > 0 ? currentImage-- : null"></div>
        <div class="gallery1-pic" v-for="(image, index) in galleryObject" :key="image.imgSrc" 
        :style="{left: `calc(50% + ${(index + (currentImage*-1))*500}px)`}">
            <img :src="image.imgSrc" />
        </div>
        <div class="gallery1-arrow" style="right:0;" @click="currentImage < galleryObject.length-1 ? currentImage++ : null"></div>
    </div>
</template>

<script>
export default {
    name: "EneftesGallery1",
    props: ["galleryObject", "baseUrl"],
    data() {
        return {
            currentImage: 0,
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

        overflow: hidden;

        

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
            width:auto;
            height:400px;
            
        }
    }
</style>
