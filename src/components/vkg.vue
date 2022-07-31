<template >
    <div class="full-keyboard" @click="setFocus" v-if="showKeyboard" >
        <div :class="[index , 'lines']"  v-for="(line, index) in language" :key="index" >
            <div 
                v-for="(key, index) in line.keys" :key="index" 
                :class="[ key == 'backspace' || key == 'keyboard_arrow_down' || key == 'space_bar' || key == 'keyboard_capslock' || key == 'keyboard_return' ? 'keys  material-symbols-outlined' : 'keys' ]" 
                :id="key" 
                @click=" [key == 'keyboard_capslock' ? Capslock = !Capslock : HandlingKeyboardButton(key) , setFocus] "
                :style="[Capslock ? 'text-transform: uppercase;' : '' , Capslock && key == 'keyboard_capslock' ? 'color:#16ff0b;' : '' ]"
            >
                    {{key}}
            </div>
        </div>
    </div>
</template>

<script>
import  languages  from '../assets/languages.js'
    export default {
        data() {
            return {
                language : languages.English,
                showKeyboard : false ,
                currentInput : null,
                currentValueInput : '',
                currentSelection : null,
                focusInput: '',
                Capslock: false,
            }
        },
        mounted () {
            addEventListener('click', (e)=>{
                this.setInputName(e)
            })
        },
        methods: {
            setInputName(e) {
                if(e.target.tagName == 'INPUT' || e.target.tagName == 'TEXTAREA'){
                    this.showKeyboard = true ;
                    this.focusInput = e.target ;
                    this.currentValueInput = e.target.value ;
                    this.currentInput = e.target._assign ;
                    this.currentSelection = e.target.selectionStart ;
                }else{
                    if(e.target.className != 'full-keyboard' && !e.target.className.includes('keys') ) this.showKeyboard = false ;
                }
            },
            HandlingKeyboardButton(key){
                if(this.currentInput){
                    switch (key) {
                        case 'backspace':
                            this.backspaceHandling();
                            break;
                        case 'keyboard_arrow_down':
                            this.showKeyboard = false ;
                            break;
                        case 'space_bar':
                            this.addValueToInput(' ');
                            break;
                        case 'keyboard_return':
                            if(this.focusInput.tagName == 'TEXTAREA') this.addValueToInput('\r') ;
                            break;
                        default:
                            this.addValueToInput(key);
                            break;
                        }
                }
            },
            setFocus(){
                this.focusInput.focus()
                this.focusInput.setSelectionRange(this.currentSelection,this.currentSelection)
            },

            addValueToInput(key){
                key = this.Capslock ?  key.toUpperCase() : key.toLowerCase();

                this.currentValueInput = 
                    this.currentValueInput.substring(0, this.currentSelection) + 
                    key + 
                    this.currentValueInput.substring(this.currentSelection)

                this.currentInput( this.currentValueInput );
                this.currentSelection++ ;
            },

            backspaceHandling(){
                this.currentValueInput =
                    this.currentValueInput.substring(0, this.currentSelection - 1) + 
                    this.currentValueInput.substring(this.currentSelection , this.currentValueInput.length);

                this.currentInput( this.currentValueInput );
                this.currentSelection -= this.currentSelection  ? 1 : 0 ;
            },
        },
    }
</script>

<style  scoped>
    .full-keyboard{
        background-color: #d6d6d6;
        width: fit-content;
        margin: auto;
        padding: 10px 40px 10px 40px;
        display: flex;
        flex-direction: column;
        align-items: center;
        z-index: 10000;
    }
    .full-keyboard .lines{
        /* margin: 5px 0px 5px 0px; */
        display: flex;
        flex-direction: row;
        flex-wrap: nowrap;
        padding: 1px 0px 1px 0px;
        /* border: 1px solid firebrick; */
    }
    .full-keyboard .keys{
        min-width: 40px; min-height: 20px;
        margin: 0px 1px 0px 1px;
        font-size: 20px;
        padding: 7px 10px 7px 10px;
        border: none;
        border-radius: 3px;
        background-color: rgba(226, 247, 253, 0.678);
    }
    #backspace { width: 40px;}
    /* #done { } */
    #space_bar { width: 300px;  }
    #keyboard_capslock { width: 40px; }
    #keyboard_return { width: 70px; }


    @import'https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0';
</style>

