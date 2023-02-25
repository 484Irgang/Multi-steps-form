<script>
    export default {
        data(){
            return{
                indexButton: 0
            }
        },
        props: {
            clicked: Array
        },
        emits: ['responseClick','responseClickBack'],
        methods: {
            clickedNext(){
                if(this.clicked[1] < 3){
                    this.indexButton = this.clicked[0];
                    this.indexButton++;
                    this.$emit('responseClick', this.indexButton);
                }
                else{
                    return false;
                }
            },
            clickedBack(){
                let indexStepBack = this.clicked[1];
                indexStepBack--;
                this.$emit('responseClickBack',indexStepBack);
            }
        }
    }
</script>

<template>
    <div class="container-button">
        <button @click="clickedNext">Next Step</button>
        <button v-show="clicked[1] > 0" @click="clickedBack">Go Back</button>
    </div>
</template>

<style scoped>
.container-button{
    width: 100%;
    max-width: 550px;
    justify-self: flex-end;
    display: flex;
    flex-direction: row-reverse;
    justify-content: space-between;
    align-items: center;
    padding: 2%;
}
.container-button button:first-of-type{
    width: 120px;
    height: 40px;
    border: none;
    border-radius: 8px;
    font-family: Ubuntu;
    font-weight: 400;
    color: #ffffff;
    background-color: #02295a;
    cursor: pointer;
    transition-duration: 0.4s;
}
.container-button button:first-of-type:hover{
    background-color: #043775;
}
.container-button button:last-of-type{
    height: 25px;
    border: none;
    background-color: transparent;
    cursor: pointer;
    font-family: Ubuntu;
    font-weight: 500;
    color: hsl(231, 11%, 63%);
    transition-duration: 0.4s;
}
.container-button button:last-of-type:hover{
    color: hsl(231, 7%, 37%);
}

@media screen and (max-width: 768px){
    .container-button{
        width: 100%;
        max-width: initial;
        padding: 2% 4%;
        background-color: hsl(231, 100%, 99%);
        position: absolute;
        bottom: 0;
        box-shadow: 4px 6px 30px -10px rgb(0 0 0 / 50%);
        
    }
}
</style>