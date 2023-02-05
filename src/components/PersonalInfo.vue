<script>
    import ButtonNext from './ButtonNext.vue'

    export default{
        components: {ButtonNext}
    }
</script>

<template>
    <div class="container-personal-info">
        <div>
            <h1>Personal Info</h1>
            <p>Please provide your name, email adress and phone number.</p>
        </div>
        <div class="form-personal-info">
            <p>Name</p>
            <input type="text" id="name" placeholder="e.g. Stephen King"/>
            <p>Email Adress</p>
            <input type="text" id="email" placeholder="e.g. stephanking@loren.com"/>
            <p>Phone Number</p>
            <input type="text" id="number" placeholder="e.g. +1 234 567 890"/>
        </div>
        <ButtonNext/>
    </div>
</template>

<style scoped>
    .container-personal-info{
        width: 70%;
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
    .form-personal-info > p{
        color: #02295a;
        margin: 6px 0;
        font-size: 12px;
        font-weight: 500;
    }
    .form-personal-info > input[type=text]{
        width: 100%;
        padding: 3%;
        border-radius: 8px;
        border: 2px solid rgb(214, 217, 230);
        margin-bottom: 18px;
        cursor: pointer;
        font-weight: 700;
        font-family: Ubuntu;
        color: #02244d;
    }
    .form-personal-info > input[type=text]:focus{
        border: 2px solid #02295a;
        outline: none;
    }
    .form-personal-info > input[type=text]::placeholder{
        font-weight: 600;
        color: rgba(150, 153, 171, 0.7);
    }

    @media screen and (max-width: 768px){
        .container-personal-info{
            width: 100%;
            height: fit-content;
            z-index: 2;
            background-color: hsl(231, 100%, 99%);
            border-radius: 16px;
            box-shadow: 4px 6px 30px -20px rgb(0 0 0 / 50%);
            padding: 5%;
            margin-top: 10%;
        }
        .form-personal-info{
            margin-top: 8%;
        }
    }
</style>