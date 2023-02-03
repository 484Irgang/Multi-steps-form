<script>
import PersonalInfo from './PersonalInfo.vue'

export default{
    components: {PersonalInfo}
}
</script>

<template>
    <div class="personal-box">
        <div class="box-steps">
            <ul>
                <li class="step step-1">
                    <span>1</span>
                    <p><span>step 1</span><br/>Personal info</p>
                </li>
                <li class="step step-2">
                    <span>2</span>
                    <p><span>step 2</span><br/>select plan</p>
                </li>
                <li class="step step-3">
                    <span>3</span>
                    <p><span>step 3</span><br/>add-ons</p>
                </li>
                <li class="step step-4">
                    <span>4</span>
                    <p><span>step 4</span><br/>summary</p>
                </li>
            </ul>
        </div>
        <PersonalInfo/>
    </div>
</template>

<style scoped>
    .personal-box{
        width: 100%;
        height: 100%;
        display: flex;
        padding: 1%;
        flex-wrap: wrap;
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
        color: #cccccc;
    }
</style>