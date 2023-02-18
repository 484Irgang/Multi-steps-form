<script>
    export default{
        props: {
            clicked: Number
        },
        watch:{
            clicked(newClicked){
                
                let validation = true;
                    const dados = document.querySelectorAll(".form-personal-info input[type=text]");
                    for(var i=0;i<dados.length;i++){
                        dados[i].style.border = "2px solid #02295a";
                        dados[i].parentNode.children[1].innerHTML = '';
                    }

                    const checkName = dados[0].value.match(/^[A-Z]{1}[a-z]{1,}[ ]{1}[A-Za-z]{1,}/g);
                    if(checkName == null){
                        dados[0].style.border = "2px solid hsl(354, 84%, 57%)";
                        dados[0].parentNode.children[1].innerText = "This field is invalid";
                        validation = false;
                    }

                    const checkEmail = dados[1].value.match(/^[A-Za-z0-9._-]{1,}[@]{1}[A-Za-z]{1,}[.]{1}[a-z]{1,}/g);
                    if(checkEmail == null){
                        dados[1].style.border = "2px solid hsl(354, 84%, 57%)";
                        dados[1].parentNode.children[1].innerText = "This field is invalid";
                        validation = false;
                    }

                    const checkNumber = dados[2].value.match(/^[+]{1}[0-9]{12,16}/);
                    if(checkNumber == null || dados[2].value.length > 16){
                        dados[2].style.border = "2px solid hsl(354, 84%, 57%)";
                        dados[2].parentNode.children[1].innerText = "This field is invalid";
                        validation = false;
                    }
                    

                    this.alterarSteps(validation,dados);
            }
        },
        methods: {
            alterarSteps(v,dados){
                this.$emit('alterarSteps', [v,dados]);
            }
        },
        emits: ['alterarSteps']
    }
</script>

<template>
    <div class="container-personal-info">
        <div>
            <h1>Personal Info</h1>
            <p>Please provide your name, email adress and phone number.</p>
        </div>
        <div class="form-personal-info">
            <div>
                <p>Name</p>
                <span></span>
                <input type="text" id="name" placeholder="e.g. Stephen King"/>
            </div>    
            <div>
                <p>Email Adress</p>
                <span></span>
                <input type="text" id="email" placeholder="e.g. stephanking@loren.com"/>
            </div>
            <div>
                <p>Phone Number</p>
                <span></span>
                <input type="text" id="number" placeholder="e.g. +1 234 567 890"/>
            </div>    
        </div>
    </div>
</template>

<style scoped>
    .container-personal-info{
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 2%;
        justify-content: space-around;
    }
    .container-personal-info > div:first-of-type{
        width: 100%;
        max-width: 450px;
    }
    .container-personal-info > div > h1{
        color: hsl(213, 96%, 18%);
    }
    .container-personal-info > div:first-of-type > p{
        color: hsl(231, 11%, 63%);
        font-weight: 400;
        margin-top: 8px;
    }
    .form-personal-info{
        width: 100%;
        max-width: 450px;
    }
    .form-personal-info > div{
        width: 100%;
        margin-bottom: 18px;
        display: flex;
        flex-wrap: wrap;
    }
    .form-personal-info > div > p{
        color: #02295a;
        margin: 6px 0;
        font-size: 12px;
        font-weight: 500;
        display: inline-block;
    }
    .form-personal-info > div > input[type=text]{
        width: 100%;
        padding: 3%;
        border-radius: 8px;
        border: 2px solid rgb(214, 217, 230);
        cursor: pointer;
        font-weight: 700;
        font-family: Ubuntu;
        color: #02244d;
    }
    .form-personal-info > div > input[type=text]:focus{
        border: 2px solid #02295a;
        outline: none;
    }
    .form-personal-info > div > input[type=text]::placeholder{
        font-weight: 600;
        color: rgba(150, 153, 171, 0.7);
    }
    .form-personal-info > div > span{
        font-size: 12px;
        align-self: center;
        margin-left: auto;
        font-weight: 500;
        font-family: Ubuntu;
        color: hsl(354, 84%, 57%);
    }

    @media screen and (max-width: 768px){
        .container-personal-info{
            padding: 4%;
        }
        .form-personal-info{
            margin-top: 8%;
        }
    }
</style>