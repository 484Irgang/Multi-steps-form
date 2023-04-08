<script>

</script>

<template>
    <section class="container-addons">
        <div class="description">
            <h1>Pick add-ons</h1>
            <p>Add-ons help enhance your gaming experience</p>
        </div>

        <div class="add-on_box">
            <label class="check">
                <input type="checkbox"/>
            </label>
            <span>Online service<br/> acess to multiplayer games</span>
            <span>+$2/mo</span>
        </div>
        

    </section>
</template>

<style scoped>
.container-addons{
    width: 100%;
    height: 100%;
    max-width: 550px;
    display: flex;
    flex-direction: column;
    padding: 2%;
    align-items: center;
}
.description{
    width: 100%;
    margin-top: 2%;
}
.description h1{
    color: hsl(213, 96%, 18%);
    font-size: 2em;
}
.description p{
    color: hsl(231, 11%, 63%);
    font-weight: 400;
    margin-top: 8px;
}
.add-on_box{
    width: 100%;
    /*background-color: red;*/
    margin-top: 5%;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    padding: 20px;
}
.add-on_box .check{
    background-color: white;
    margin-right: 18px;
    border-radius: 4px;
    height: 16px;
}
.add-on_box .check input{
    appearance: none;
    width: 16px;
    height: 16px;
    border-radius: 4px;
    border: 0.5px solid #DBDADF;
}
.add-on_box .check input:checked{
    clip-path: polygon(0% 0%,100% 0%, 100% 100%, 46% 100%, 46% 74%, 89% 32%, 76% 21%, 44% 53%, 25% 41%, 13% 54%, 46% 74%, 46% 100%, 0% 100%);
    background-color: #4C45FF;
}
.add-on_box span{
    background-color: blue;
}
.add-on_box span:last-of-type{
    background-color: yellow;
    margin-left: auto;
}
.teste{
    width: 500px;
    height: 500px;
    background-color: aqua;
}
</style>