<template>
    <section class="new-window"
    ref="sectionContainer"
    :class="{fullscreen: fullscreen}"
    :style="[{top: windowedComponent.top, left: windowedComponent.left},
    fullscreen ? {top: '50vh', left: '50vw'} : {height: windowedComponent.height, width: windowedComponent.width, top: windowedComponent.top, left: windowedComponent.left}]">
        
        <header @mousedown="!fullscreen && dragMouseDown($event)">
            {{windowedComponent.component}}
            <button class="close-x" @click="windowedComponent.isActive = false">
                <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512"><title>Close</title><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32" d="M368 368L144 144M368 144L144 368"/></svg>
            </button>
            <button class="fullscreen-btn" @click="fullscreen = !fullscreen">
                <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512"><title>Resize</title><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32" d="M304 96h112v112M405.77 106.2L111.98 400.02M208 416H96V304"/></svg>
            </button>
        </header>

        <nav v-if="windowedComponent.browser">
            <div class="url-container">
                www.{{windowedComponent.component}}.com/
            </div>
        </nav>

        <slot>
        </slot>
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

<style scoped>
    .new-window {
        background:black;
        position:absolute;
        transform:translate(-50%, -50%);
        border:3px solid rgb(49, 49, 49);
        transition: width 1s, height 1s;
    }

    .fullscreen {
        height:calc(100% - 6px);
        width:calc(100% - 6px);
        transition: top 1s, left 1s, width 1s, height 1s;
    }

    header {
        height:15px;
        border-bottom: 3px solid rgb(49, 49, 49);
        color:white;
        text-align: center;
        font-family:cascadiaCode;
    }

    nav {
        position: relative;
        border-bottom: 3px solid white;
        width:100%;
        height:50px;
    }

    .url-container {
        height:40px;
        width:80%;
        font-size:2em;

        position:absolute;
        top:50%;
        left:5px;
        transform:translateY(-50%);
        border:1px solid black;
    }

    button {
        position:relative;
        float:right;
        height:15px;
        width:15px;
        border:none;
        border-radius:50%;
        margin-right:5px;
    }

    .fullscreen-btn {
        background:blue;
    }

    .close-x {
        background:red;
    }

    svg {
        position:absolute;
        top:50%;
        left:50%;
        transform:translate(-50%,-50%) scale(3);
    }

</style>