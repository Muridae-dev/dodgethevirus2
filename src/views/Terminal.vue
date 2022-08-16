<template>
    <div class="terminal-container" @click="focusInput">
        <div class="input-text">
            <span v-for="(writtenCommand, index) in writtenCommands" :key="index">
                {{writtenCommand}}
            </span>
        </div>
        ><input type="text" class="terminal-input" name="terminal-input" ref="terminalInput">
    </div>
</template>

<script>
/* 
  UPCOMING FEATURES:
    cd ./dragonslair
        - sort()
            This sorts the questions by website name
        - bribe(amount)
            This is only usable when there are over 1/3 of questions left
            Per 1000 credits, removes 1 question

        CHEATS:
            - reduce()
                This reduces the questions by half
*/
export default {
    name: "Terminal",
    data() {
        return {
            writtenCommands: []
        }
        
    },
    methods: {
        focusInput() {
            this.$refs.terminalInput.focus()
        },
        enterPressed() {
            if(this.$refs.terminalInput.value == "scan()") {
                this.writtenCommands.push("scanning...");
            }
            else {
                this.writtenCommands.push("command not found: " + this.$refs.terminalInput.value);
            }
            
            this.$refs.terminalInput.value = "";
        }
    },
    created() {
        window.addEventListener('keypress', (e) => {
            if(e.key === "Enter") {
                this.enterPressed();
            }
        })
    }
}
</script>

<style scoped>
    .terminal-container {
        height:100%;
        width:100%;
        background:black;
        color:rgb(0, 255, 65);

        font-family:cascadiaCode;
    }

    .terminal-input {
        height:auto;
        width:98%;

        border: none;
        background-color: transparent;
        resize: none;
        outline: none;
        caret-color: white;

        font-family: cascadiaCode;
        color:rgb(0, 255, 65);
        font-size:1em;

    }

    span {
        display:block;
    }
</style>