<script>
    export default{
        data(){
            return{
                periodPlanYear: false,
                planSelected: {},
                toggleAlert: false,
                plan_choiced: null
            }
        },
        methods: {
            choicePlan(value){
                this.plan_choiced = value;
                this.planSelected = {type: value};
            },
            objIsEmpty(obj){
                for(var prop in obj){
                    if(obj.hasOwnProperty(prop))
                        return false;
                }
                return true;
            }
        },
        props: {
            clicked: Number,
            indexStep: Number
        },
        watch: {
            clicked(newClicked){
                if(this.indexStep == 1){
                    if(this.objIsEmpty(this.planSelected)){
                        this.toggleAlert = true;
                        setTimeout(() => this.toggleAlert = false, 5000);
                    }
                    else{
                        let plan = document.querySelectorAll(".plans .plan");
                        let type = plan[this.plan_choiced].children[1].innerText.split('\n')[0];
                        let price = parseInt(plan[this.plan_choiced].children[1].innerText.split('\n')[2].split("/")[0].split("$")[1], 10);
                        let period = this.periodPlanYear;

                        this.planSelected = {name: type, price: price, periodYear: period};

                        this.$emit('sendPlan',this.planSelected);
                    }
                }
                else{
                    return false;
                }
            }
        }

    }
</script>

<template>
    <section class="container-select-plan">
        <div class="description">
            <h1>Select your plan</h1>
            <p>You have the option of monthly or yearly billing</p>
        </div>

        <div class="plans">
            <div :class="{planSelected: plan_choiced == 0}" @click="choicePlan(0)" class="plan">
                <img src="../assets/icon-arcade.svg" class="img-plan"/>
                <p>Arcade<p v-if="this.periodPlanYear">$90/yr</p><p v-else>$9/mo</p><p v-show="periodPlanYear"> 2 months free</p></p>
            </div>

            <div :class="{planSelected: plan_choiced == 1}" @click="choicePlan(1)" class="plan">
                <img src="../assets/icon-advanced.svg" class="img-plan"/>
                <p>Advanced<p v-if="this.periodPlanYear">$120/yr</p><p v-else>$12/mo</p><p v-show="periodPlanYear">2 months free</p></p>
            </div>

            <div :class="{planSelected: plan_choiced == 2}" @click="choicePlan(2)" class="plan">
                <img src="../assets/icon-pro.svg" class="img-plan"/>
                <p>Pro<p v-if="this.periodPlanYear">$150/yr</p><p v-else>$15/mo</p><p v-show="periodPlanYear">2 months free</p></p>
            </div>
        </div>

        <div class="period-plan">
            <div>
                <span :class="{periodSelected: !periodPlanYear}">Monthly</span>
                <div @click="() => this.periodPlanYear = !this.periodPlanYear"><span :class="{scrollRight : periodPlanYear, scrollLeft: !periodPlanYear}" class="circle"></span></div>
                <span :class="{periodSelected: periodPlanYear}">Yearly</span>
            </div>
        </div>

        <div v-show="toggleAlert" :class="{toggleAlert: toggleAlert}" class="alert">You need select some plan</div>
    </section>
</template>

<style scoped >
    .container-select-plan{
        width: 100%;
        height: 100%;
        max-width: 550px;
        display: flex;
        flex-direction: column;
        padding: 2%;
        align-items: center;
    }
    .container-select-plan > div{
        margin-top: 5%;
    }
    .container-select-plan > div:last-of-type{
        margin-top: 10%;
    }
    .description{
        width: 100%;
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

    .plans{
        width: 100%;
        display: flex;
        justify-content: space-between;
    }

    .plans .plan{
        width: 30%;
        aspect-ratio: 6/7;
        border: 1px solid #c7c9d6;
        border-radius: 8px;
        padding: 3%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        cursor: pointer;
    }
    .plans .plan:hover:not(.planSelected){
        border: 1px solid #02295a;
    }
    .plans .planSelected{
        border: 2px solid #02295a;
        background-color: #edeef387;
    }
    .plans .plan .img-plan{
        width: 44px;
        height: 44px;
        /* background-color: blue; */
        border-radius: 50%;
    }
    .plans .plan > p{
        color: #02295a;
        font-weight: 500;
    }
    .plans .plan p > p:first-of-type{
        font-weight: 400;
        font-size: 14px;
        color: #9699ab;
    }
    .plans .plan p > p:last-of-type{
        font-weight: 500;
        font-size: 12px;
    }
    .period-plan{
        width: 100%;
        padding: 3%;
        display: flex;
        justify-content: center;
        background-color: hsl(233, 100%, 98%);
    }
    .period-plan > div{
        width: 100%;
        max-width: 250px;
        /* background-color: green; */
        display: flex;
        justify-content: space-around;
        align-items: center;
        font-weight: 500;
        color: hsl(231, 11%, 63%);
    }
    .period-plan > div > div{
        width: 54px;
        height: 27px;
        border-radius: 16px;
        background-color: #02295a;
        padding: 2%;
        display: flex;
        align-items: center;
        cursor: pointer;
    }
    .period-plan > div > div > .circle{
        display: inline-block;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        background-color: white;
        
    }
    .period-plan > div > div .scrollRight{
        animation-name: scrollRight;
        animation-duration: 0.7s;
        animation-fill-mode: forwards;
    }
    .period-plan > div > div .scrollLeft{
        animation-name: scrollLeft;
        animation-duration: 0.7s;
        animation-fill-mode: forwards;
    }
    .period-plan > div .periodSelected{
        color: #02295a;
    }
    .alert{
        width: 100%;
        max-width: 300px;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: rgb(255, 207, 207);
        border: 1px solid red;
        color: rgb(162, 9, 9);
        position: absolute;
        bottom: 0;
        padding: 8px;
        border-radius: 12px;
        box-shadow: 0 0 10px 2px rgba(187, 99, 99, 0.342);
    }
    .toggleAlert{
        animation-name: alertOn;
        animation-duration: 2s;
        animation-fill-mode: forwards;
    }
    @keyframes scrollRight{
        from{
            transform: translateX(0) rotateY(0deg);
        }
        to{
            transform: translateX(120%) rotateY(180deg);
        }
    }

    @keyframes scrollLeft{
        from{
            transform: translateX(120%) rotateY(180deg);
        }
        to{
            transform: translateX(0) rotateY(0deg);
        }
    }

    @keyframes alertOn{
        0%{
            bottom: 0;
        }
        15%{
            bottom: 22%;
        }
        30%{
            bottom: 20px;
        }
        50%{
            bottom: 22%;
        }
        70%{
            bottom: 100px;
        }
        100%{
            bottom: 22%;
        }
    }

    @media screen and (max-width: 478px){
        .plans{
            flex-direction: column;
        }
        .plans .plan{
            width: 100%;
            padding: 4%;
            margin-top: 2%;
            aspect-ratio: auto;
            flex-direction: row;
            justify-content: start;
        }
        .plans .plan p{
            margin-left: 5%;
        }
    }
</style>