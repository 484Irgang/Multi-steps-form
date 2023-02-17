<script>
    export default {
        data(){
            return{
                indexButton: 0
            }
        },
        props: {
            clicked: Number
        },
        emits: ['responseClick'],
        methods: {
            clickedNext(){
                this.indexButton = this.clicked;
                this.indexButton++
                this.$emit('responseClick', this.indexButton);
            }
        }
    }
</script>

<template>
    <div class="container-button">
        <button @click="clickedNext">Next Step</button>
        <button>Go Back</button>
    </div>
</template>

<style scoped>
.container-button{
    width: 100%;
    max-width: 450px;
    justify-self: flex-end;
    display: flex;
    flex-direction: row-reverse;
    justify-content: space-between;
    align-items: center;
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
    }
}
</style>