<script></script>

<template>
    <section class="container-select-plan">
        <div class="description">
            <h1>Select your plan</h1>
            <p>You have the option of monthly or yearly billing</p>
        </div>

        <div class="plans">
            <div class="plan">
                <img :src="'./src/assets/icon-arcade.svg'" class="img-plan"/>
                <p>Arcade<br/><span>$9/mo</span><br/><span> 2 months free</span></p>
            </div>

            <div class="plan">
                <img :src="'./src/assets/icon-advanced.svg'" class="img-plan"/>
                <p>Advanced<br/><span>$9/mo</span><br/><span>2 months free</span></p>
            </div>

            <div class="plan">
                <img :src="'./src/assets/icon-pro.svg'" class="img-plan"/>
                <p>Pro<br/><span>$9/mo</span><br/><span>2 months free</span></p>
            </div>
        </div>

        <div class="period-plan">
            <div>
                <span>Monthly</span>
                <div><span class="circle"></span></div>
                <span>Yearly</span>
            </div>
        </div>

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
        border: 1px solid #02295a;
        border-radius: 8px;
        padding: 3%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        cursor: pointer;
    }
    .plans .plan:hover{
        background-color: #f0f6ff;
    }
    .plans .plan .img-plan{
        width: 44px;
        height: 44px;
        /* background-color: blue; */
        border-radius: 50%;
    }
    .plans .plan p{
        color: #02295a;
        font-weight: 500;
    }
    .plans .plan p > span:first-of-type{
        font-weight: 400;
        font-size: 14px;
        color: #9699ab;
    }
    .plans .plan p > span:last-of-type{
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
        max-width: 200px;
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
    }
    .period-plan > div > div > .circle{
        display: inline-block;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        background-color: white;
        cursor: pointer;
    }

    @media screen and (max-width: 478px){
        .plans{
            flex-direction: column;
        }
        .plans .plan{
            width: 100%;
            padding: 4%;
            margin-top: 4%;
            aspect-ratio: auto;
            flex-direction: row;
            justify-content: start;
        }
        .plans .plan p{
            margin-left: 5%;
        }
    }
</style>