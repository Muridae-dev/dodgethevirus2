<template>
    <nav :style="navHidden ? {top: '-50px'} : {top: '30px'}">
        <a v-for="link in linkObject">
            {{link.text}}
        </a>
    </nav>
</template>

<script>
    export default {
        props: ["linkObject", "componentName"],
        data() {
        return {
            // THESE THREE ARE USED FOR HIDING THE MENU ON SCROLL DOWN
            newScrollY: 0,
            oldScrollY: 0,
            navHidden: false,

        }
    },
    mounted () {
        // EVENT LISTENER TO HIDE MENU ON SCROLLING DOWN & SHOW ON SCROLL UP
        console.log(this.componentName)
        let kahunaContainer = document.querySelector(`#component-container-${this.componentName}`);
        kahunaContainer.addEventListener('scroll', (e) => {
            // GET THE NEW SCROLL VALUE
            this.newScrollY = kahunaContainer.scrollTop;
            // IF WE'VE SCROLLED PASSED THE NAV:S HEIGHT
            // AND THE NEW SCROLL IS LARGER THAN THE OLD SCROLL
            // AKA WE ARE SCROLLING DOWN
            if(this.newScrollY > this.oldScrollY) {
                // WE HIDE THE NAV
                this.navHidden = true;
            }
            // VICE VERSA
            else {
                this.navHidden = false;
            }
            console.log('newscroll', this.newScrollY);
            console.log('oldscroll', this.oldScrollY);
            console.log(this.navHidden)

            // UPDATE OLD SCROLL AT THE END TO COMPARE AFTER NEXT SCROLL
            this.oldScrollY = kahunaContainer.scrollTop;
            
        });
        
    },
    destroyed () {
        // EVENT LISTENER TO HIDE MENU ON SCROLLING DOWN & SHOW ON SCROLL UP
        console.log(this.componentName)
        let kahunaContainer = document.querySelector(`#component-container-${this.componentName}`);
        kahunaContainer.removeEventListener('scroll', (e) => {
            // GET THE NEW SCROLL VALUE
            this.newScrollY = kahunaContainer.scrollTop;
            // IF WE'VE SCROLLED PASSED THE NAV:S HEIGHT
            // AND THE NEW SCROLL IS LARGER THAN THE OLD SCROLL
            // AKA WE ARE SCROLLING DOWN
            if(kahunaContainer.scrollTop > 50 && this.newScrollY > this.oldScrollY) {
                // WE HIDE THE NAV
                this.navHidden = true;
            }
            // VICE VERSA
            else {
                this.navHidden = false;
            }
            console.log('newscroll', this.newScrollY);
            console.log('oldscroll', this.oldScrollY);
            console.log(this.navHidden)

            // UPDATE OLD SCROLL AT THE END TO COMPARE AFTER NEXT SCROLL
            this.oldScrollY = kahunaContainer.scrollTop;
            
        });
        
    },
    }
</script>

<style lang="scss" scoped>
    nav {
        height:40px;
        padding-top:5px;
        padding-bottom:5px;
        width:100%;
        position:fixed;
        background:black;
        border-bottom:2px solid white;
        z-index:12;
        text-align: center;
        display:flex;
        justify-content:space-evenly;
        align-items: baseline;
        transition:top 1s;
        transition-timing-function:ease;

        a {
            font-size:2em;
            font-family:PhonkRegular;
            width:20%;
        }
    }
</style>