<template>
    <section class="new-window"
    ref="sectionContainer"
    :class="{fullscreen: fullscreen}"
    :style="[{top: windowedComponent.top, left: windowedComponent.left},
    fullscreen ? {top: '50vh', left: '50vw'} : {height: windowedComponent.height, width: windowedComponent.width, top: windowedComponent.top, left: windowedComponent.left}]">
        
        <!--<header @mousedown="!fullscreen && dragMouseDown($event)">
            {{windowedComponent.component}}
            <button class="close-x" @click="windowedComponent.isActive = false">
                <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512"><title>Close</title><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32" d="M368 368L144 144M368 144L144 368"/></svg>
            </button>
            <button class="fullscreen-btn" @click="fullscreen = !fullscreen">
                <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512"><title>Resize</title><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32" d="M304 96h112v112M405.77 106.2L111.98 400.02M208 416H96V304"/></svg>
            </button>
        </header>-->

        <nav v-if="windowedComponent.browser">
            <div class="url-container">
                www.{{windowedComponent.component}}.com/

                <button class="close-x" @click="windowedComponent.isActive = false">
                    <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512"><title>Close</title><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32" d="M368 368L144 144M368 144L144 368"/></svg>
                </button>
                <button class="fullscreen-btn" @click="fullscreen = !fullscreen">
                    <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512"><title>Resize</title><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32" d="M304 96h112v112M405.77 106.2L111.98 400.02M208 416H96V304"/></svg>
                </button>
            </div>


        </nav>

        <div class="component-container" :id="`component-container-${windowedComponent.component}`" ref="componentContainer">
            <slot>
            </slot>
        </div>
    </section>
</template>

<script>
export default {
    name: "NewWindow",
    props: ["windowedComponent"],
    data() {
        return {
            fullscreen: false,

            // FOR DRAG
            positions: {
                clientX: undefined,
                clientY: undefined,
                movementX: 0,
                movementY: 0
            }
        }
    },
    methods: {
        // -------------------- DRAG FUNCTIONS --------------------
        dragMouseDown: function(e) {
            e.preventDefault();
            this.positions.clientX = e.clientX;
            this.positions.clientY = e.clientY;
            document.onmousemove = this.startDrag;
            document.onmouseup = this.stopDrag;
        },
        startDrag: function(e) {
            this.positions.movementX = this.positions.clientX - e.clientX;
            this.positions.movementY = this.positions.clientY - e.clientY;
            this.positions.clientX = e.clientX;
            this.positions.clientY = e.clientY;
            this.$refs.sectionContainer.style.top = (this.$refs.sectionContainer.offsetTop - this.positions.movementY) + "px";
            this.$refs.sectionContainer.style.left = (this.$refs.sectionContainer.offsetLeft - this.positions.movementX) + "px";
        },
        stopDrag() {
            document.onmouseup = null;
            document.onmousemove = null;
        }
        // --------------------      END       --------------------
    }
}
</script>

<style lang="scss" scoped>

    $border-color: rgb(195, 231, 255);

    .component-container::-webkit-scrollbar-track
    {
        border-radius:10px;
        -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
        background-color: black;
        
    }

    .component-container::-webkit-scrollbar
    {
        width: 10px;
        background-color: rgb(0, 0, 0);
    }

    .component-container::-webkit-scrollbar-thumb
    {
        background-color: $border-color;
        border: 2px solid $border-color;
    }


    .new-window {
        background:black ;
        position:absolute;
        transform:translate(-50%, -50%);
        border-radius:5px;
        transition: width 1s, height 1s, top 1s, left 1s;
        overflow: hidden;
    }

    .component-container {
        position:relative;
        width:100%;
        height:calc(100% - 31px);
        overflow-y:scroll;
    }

    .fullscreen {
        height:calc(100%);
        width:calc(100% - 6px);
        transition: top 1s, left 1s, width 1s, height 1s;
    }

    nav {
        position: sticky;
        top:0px;
        width:100%;
        height:30px;
        font-family:RussoOne;
        z-index:99;
        background: black;
    }

    .url-container {
        height:30px;
        width:calc(100% - 5px);
        font-size:1.5em;

        position:relative;
        top:0;
        left:5px;
        overflow-x:hidden;  
        
    }

    button {
        position:relative;
        float:right;
        height:50%;
        width:auto;
        border:none;
        cursor: pointer;
    }

    .fullscreen-btn {
        background:black;
        right:45px;
        top:7%;
        transform:translateY(-50%) scale(1.7);
    }

    .close-x {
        background:black;
        right:30px;
        transform:translateY(-50%) scale(2);
    }

    svg {
        position:absolute;
        width:auto;
        height:100%;
        color:white;
    }

</style>
