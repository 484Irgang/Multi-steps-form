<script>
import PersonalInfo from './PersonalInfo.vue'
import SelectPlan from './SelectPlan.vue'
import ButtonNext from './ButtonNext.vue'
import Addons from './PickAddons.vue'

export default{
    data(){
        return {
            stepIndex : 0,
            buttonClick: 0
        }
    },
    components: {PersonalInfo,SelectPlan,ButtonNext,Addons},
    methods: {
        checarPersonalInfo(e){
            e[0]? this.stepIndex++ : false;
        },
        checkStepPlan(e){
            this.stepIndex++;
        },
        returnedButtonNext(e){
            this.buttonClick = e;
        },
        returnedButtonBack(e){
            this.stepIndex = e;
        }
    }
}
</script>

<template>
    <div class="personal-box">
        <div class="box-steps">
            <ul>
                <li class="step step-1">
                    <span :class="{selected : stepIndex == 0}">1</span>
                    <p><span>step 1</span><br/>Personal info</p>
                </li>
                <li class="step step-2">
                    <span :class="{selected : stepIndex == 1}">2</span>
                    <p><span>step 2</span><br/>select plan</p>
                </li>
                <li class="step step-3">
                    <span :class="{selected : stepIndex == 2}">3</span>
                    <p><span>step 3</span><br/>add-ons</p>
                </li>
                <li class="step step-4">
                    <span :class="{selected : stepIndex == 3}">4</span>
                    <p><span>step 4</span><br/>summary</p>
                </li>
            </ul>
        </div>
        <div class="container-form">
            <PersonalInfo v-show="stepIndex == 0" @liberarStep = "(e) => checarPersonalInfo(e)" :clicked="buttonClick" :indexStep="stepIndex"/>
            <SelectPlan v-show="stepIndex == 1" :clicked="buttonClick" :indexStep="stepIndex" @sendPlan="(e) => checkStepPlan(e)"/>
            <Addons v-show="stepIndex == 2" />    
            <ButtonNext @responseClick="(e) => returnedButtonNext(e)" :clicked="[buttonClick,stepIndex]" @responseClickBack="(e) => returnedButtonBack(e)"/>
        </div>    
    </div>
</template>

<style scoped>
    .personal-box{
        display: flex;
        padding: 1%;
        justify-content: space-between;
    }
    .box-steps{
        width: 30%;
        height: 100%;
        min-width: 250px;
        max-width: 250px;
        height: 100%;
        background-image: url("../assets/bg-sidebar-desktop.svg");
        background-size: cover;
        background-repeat: no-repeat;
        border-radius: 12px;
        padding-top: 2%;
    }
    .step{
        list-style: none;
        /* background-color: green; */
        margin-top: 20px;
        display: flex;
        color: #EEF5FF;
        justify-content: space-around;
    }
    .step > span{
        width: 40px;
        aspect-ratio: 1;
        border: 1px solid #EEF5FF;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 18px;
    }
    .step .selected{
        background-color:hsl(206, 94%, 87%);
        color: black;
    }
    .step > p{
        /* background-color: blue; */
        min-width: 160px;
        text-transform: uppercase;
        font-size: 12px;
        font-weight: 500;
    }
    .step > p > span{
        font-size: 10px;
        display: inline-block;
        margin: 4px 0;
        color: #a3a3a3;
    }
    .container-form{
        padding: 2%;
        width: 70%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
    }

    @media screen and (max-width: 768px){
        .box-steps{
            width: 100%;
            height: 30%;
            max-width: initial;
            max-height: 200px;
            border-radius: 0;
            padding-top: 0;
            position: absolute;
            top: 0;
            left: 0;
            z-index: 1;
            background-image: url("../assets/bg-sidebar-mobile.svg");
        }
        .box-steps ul{
            display: flex;
            justify-content: center;
        }
        .step{
            margin: 30px 10px;
        }
        .step > p{
            display: none;
        }
        .container-form{
            width: 100%;
            height: fit-content;
            z-index: 2;
            padding: 4%;
            background-color: hsl(231, 100%, 99%);
            border-radius: 16px;
            box-shadow: 4px 6px 30px -20px rgb(0 0 0 / 50%);
            margin-top: 60px;
    }
    }
</style>