<script>
    export default{
        data(){
            return {
                add_ons: [{type: "Online service", value: 1},{type: "Larger storage", value: 2},{type: "Customizable profile", value: 2}]
            }
        },
        methods: {
            choiceAdd(e,i){
                if(e.target.type == "checkbox")
                    e.preventDefault();
                console.log(e.target.defaultChecked);
                var input_check = document.querySelectorAll(".add-on_box .check input");
                input_check[i].defaultChecked = !input_check[i].defaultChecked;
                var addon_box = document.querySelectorAll(".add-on_box");
                addon_box[i].style.backgroundColor = input_check[i].defaultChecked ? "hsl(217, 100%, 97%)" : "transparent";
            }
        },
        computed: {
            checkedOrNot(){
                return false;
            }
        }
    }
</script>

<template>
    <section class="container-addons">
        <div class="description">
            <h1>Pick add-ons</h1>
            <p>Add-ons help enhance your gaming experience</p>
        </div>

        <div class="add-on_box" @click="(e) => choiceAdd(e,0)">
            <label class="check">
                <span :class="{checked: checkedOrNot}"></span>
                <input type="checkbox"/>
            </label>
            <label class="alt"><p>{{ add_ons[0].type }}</p><p>Acess to multiplayer games</p></label>
            <span>+${{ add_ons[0].value }}/mo</span>
        </div>

        <div class="add-on_box" @click="(e) => choiceAdd(e,1)">
            <label class="check">
                <input type="checkbox"/>
            </label>
            <label class="alt"><p>{{ add_ons[1].type }}</p><p>Extra 1 TB of cloud save</p></label>
            <span>+${{ add_ons[1].value }}/mo</span>
        </div>

        <div class="add-on_box" @click="(e) => choiceAdd(e,2)">
            <label class="check">
                <input type="checkbox"/>
            </label>
            <label class="alt"><p>{{ add_ons[2].type }}</p><p>Custom theme on your profile</p></label>
            <span>+${{ add_ons[2].value }}/mo</span>
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
    color: #02295a;
    font-size: 2em;
}
.description p{
    color: hsl(231, 11%, 63%);
    font-weight: 400;
    margin-top: 8px;
    margin-bottom: 2.5%;
}
.add-on_box{
    width: 100%;
    min-width: 311px;
    margin-top: 2.5%;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    padding: 0.8em;
    border: 1px solid #473dff;
    border-radius: 6px;
    cursor: pointer;
}
.add-on_box .check{
    position: relative;
    background-color: white;
    margin-right: 0.8em;
    border-radius: 4px;
    height: 16px;
    width: 16px;
}
.add-on_box .check input{
    appearance: none;
    width: 100%;
    height: 100%;
    border-radius: 4px;
    border: 0.5px solid #DBDADF;
    cursor: pointer;
}
.add-on_box .checked{
    width: 100%;
    height: 100%;
    position: absolute;
    border-radius: 4px;
    cursor: pointer;
    clip-path: polygon(0% 0%,100% 0%, 100% 100%, 46% 100%, 46% 74%, 89% 32%, 76% 21%, 44% 53%, 25% 41%, 13% 54%, 46% 74%, 46% 100%, 0% 100%);
    background-color: #4C45FF;
}
.add-on_box .alt{
     cursor: pointer;
}
.add-on_box .alt p:first-of-type{
    font-weight: 500;
    color: #02295a;
}
.add-on_box .alt p:last-of-type{
    color: #bababa;
    font-size: 0.9em;
    font-weight: 400;
}
.add-on_box span:last-of-type{
    color: #473dff;
    margin-left: auto;
    font-size: 0.9em;
}
.teste{
    width: 500px;
    height: 500px;
    background-color: aqua;
}
</style>