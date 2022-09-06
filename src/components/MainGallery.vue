<template>
    <div class="main-gallery-container">

        <div class="main-gallery-arrow arrow-left" style="left:0;" @click="currentImage > 0 ? currentImage-- : null">
            <img :src="require('../assets/icons/arrow.svg')" />
        </div>

        <div class="main-gallery-image-container" v-for="(image, index) in galleryObject" :key="index" 
        :style="{left: `calc(${(index + (currentImage*-1))*100}%)`}">
            <div class="main-gallery-side-text-container" style="left:7%;">
                <div class="main-gallery-side-text">
                    NEWS!
                </div> 
            </div>

            <div class="main-gallery-image-description" v-if="image.description">
                {{image.description}}
            </div>
            <img :src="image.imgSrc" />

            <div class="main-gallery-side-text-container" style="right:7%">
                <div class="main-gallery-side-text">
                    NEWS!
                </div> 
            </div>
        </div>

        <div class="main-gallery-arrow arrow-right" style="right:0;" @click="currentImage < (galleryObject.length - 1) ? currentImage++ : null">
            <img :src="require('../assets/icons/arrow.svg')" />
        </div>

    </div>
</template>

<script>
    export default {
        props: ["galleryObject"],
        data() {
            return {
                currentImage:0,
            }
        }
    }
</script>

<style lang="scss" scoped>
    .main-gallery-container {
        position: relative;
        height:100%;
        width:100%;
        background:black;
        overflow:hidden;

        .main-gallery-arrow {
            position:absolute;
            height:100%;
            width:7%;
            top:50%;
            transform:translateY(-50%);
            background:rgba(0, 0, 0, 0.3);
            z-index: 1;
            

            img {
                width:50%;
                position: absolute;
                top:50%;
                left:50%;
                filter: invert(100%);
            }
        }

        .arrow-left {
            left:0;

            img {
                transform: translate(-50%,-50%) rotate(-90deg);
            }
        }

        .arrow-right {
            right:0;

            img {
                transform: translate(-50%,-50%) rotate(90deg);
            }
        }

        .main-gallery-image-container {
            height:100%;
            width:100%;
            overflow:hidden;
            z-index:0;
            transition:left 1s;
            transition-timing-function:ease;

            position:absolute;

            .main-gallery-side-text-container {
                position:absolute;
                width:10%;
                height:100%;
                background:rgb(0, 0, 0);

                writing-mode: vertical-rl;
                text-orientation: upright;
                letter-spacing:0.3em;

                font-size:4em;
                font-family:Glusp;
                color:gold;
                z-index:2;

                .main-gallery-side-text {
                    position:absolute;
                    top:50%;
                    left:50%;
                    transform: translate(-50%, -50%);
                }
            }

            .main-gallery-image-description {
                position:absolute;
                left:20%;
                top:5%;
                width:40%;
                height:auto;
                background:rgba(0, 0, 255, 0.46);
                border-radius:50%;
                z-index:9;

                font-size:4em;
                color:gold;
                text-shadow: 2px 2px black;
                font-family:PhonkRegular;
                text-align:center;

                transform: rotate(-8deg);

            }

            img {
                width:auto;
                height:100%;
                position:absolute;
                left:50%;
                transform: translateX(-50%);
            }
        }
    }
</style>