<script>
    export default{
        data(){
            return {
                plan_summary: [{}, []]
            }
        },
        computed: {
            planPrice(){
                return this.plan_summary[0].periodYear? "$"+this.plan_summary[0].price+"/yr":"$"+this.plan_summary[0].price+"/mo";
            },
            planName(){
                return this.plan_summary[0].periodYear? this.plan_summary[0].name+"(Yearly)":this.plan_summary[0].name+"(Monthly)"
            },
            calcTotal(){
                if(this.plan_summary[1].length == 0){
                    return this.plan_summary[0].periodYear? "$"+this.plan_summary[0].price+"/yr":"$"+this.plan_summary[0].price+"/mo"
                }
                else{
                    var total = 0;
                    this.plan_summary[1].forEach(addon => {
                        total += addon.value;
                    });    
                        total += this.plan_summary[0].price;
                    return this.plan_summary[0].periodYear? "$"+total+"/yr":"$"+total+"/mo"
                }
            }
        },
        methods: {
            objIsEmpty(obj){
                for(var prop in obj){
                    if(obj.hasOwnProperty(prop))
                        return false;
                }
                return true;
            }
        },
        props: {
            planComplete: Object,
            addonsComplete: Array
        },
        watch: {
            planComplete(newPlan){
                this.plan_summary[0] = newPlan;
            },
            addonsComplete(newAddons){
                this.plan_summary[1] = newAddons;
            }
        }
    }
</script>

<template>

    <section class="container_summary">
        <div class="description">
            <h1>Finishing up</h1>
            <p>Doouble-check everything looks OK before confirming</p>
        </div>

        <article class="summary">
            <div v-if="objIsEmpty(plan_summary[0])" class="plan_empty">
                <p>No one plan choiced</p>
            </div>
            <div v-else class="plan">
                <label>
                    <p>{{planName}}</p>
                    <p>Change</p>
                </label>
                <span>{{planPrice}}</span>
            </div>

            <div v-if="plan_summary[1].length == 0" class="add_ons_empty">
                <p>No add ons adicionated to your plan</p>
            </div>
            <div v-else v-for="addons in plan_summary[1]" class="add_ons">
                <p>{{addons.detail}}</p>
                <span>{{plan_summary[0].periodYear? "$"+addons.value+"/yr":"$"+addons.value+"/mo"}}</span>
            </div>
        </article>

        <footer v-if="objIsEmpty(plan_summary[0])" class="total_empty">
            <p>Nothing to calc</p>
        </footer>
        <footer v-else class="total">
            <p>{{plan_summary[0].periodYear? "Total (per year)":"Total (per month)"}}</p>
            <span>{{calcTotal}}</span>
        </footer>

    </section>

</template>

<style scoped>
.container_summary{
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
.summary{
    background-color: #f7f7f7;
    width: 100%;
    margin-top: 2%;
    padding: 3.4%;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
}
.summary .plan{
    width: 100%;
    display: flex;
    padding-bottom: 4%;
    justify-content: space-between;
    align-items: center;
    border-bottom: 2px solid #e9e9e9;
}
.summary .plan > label > p:first-of-type{
    font-weight: 500;
    color: #02295a;
}
.summary .plan > label > p:last-of-type{
    color: #c6c6c6;
    font-weight: lighter;
    border-bottom: 1px solid #8c8c8c;
    margin-top: 4px;
    font-size: 14px;
    display: inline-block;
    cursor: pointer;
}
.summary .plan > label > p:last-of-type:hover{
    color: #8c8c8c;
}
.summary .plan > span{
    color: #02295a;
    cursor: default;
    font-weight: 500;
}
.summary .plan_empty{
    padding-bottom: 3.5%;
    display: flex;
    justify-content: center;
    border-bottom: 2px solid #e9e9e9;
}
.summary .plan_empty > p{
    color:#02295a;
}
.summary .add_ons{
    width: 100%;
    display: flex;
    padding: 3.5% 0;
    justify-content: space-between;
    align-items: center;
}
.summary .add_ons > p{
    color: #c6c6c6;
    cursor: default;
    font-weight: lighter;
    font-size: 15px;
}
.summary .add_ons > span{
    color: #02295a;
    cursor: default;
    font-weight: 400;
}
.summary .add_ons_empty{
    width: 100%;
    display: flex;
    padding-top: 3.5%;
    justify-content: center;
    align-items: center;
}
.summary .add_ons_empty > p{
    color: #d1d1d1;
}
.total{
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 3.5%;
}
.total > p{
    color: #c6c6c6;
    cursor: default;
    font-weight: lighter;
    font-size: 15px;
}
.total > span{
    color: #483EFF;
    cursor: default;
    font-weight: 700;
    font-size: 20px;
}
.container_summary > .total_empty{
    width: 100%;
    padding: 3.5%;
    display: flex;
    justify-content: center;
    background-color: #022a5a8b;
}
.container_summary > .total_empty > p{
    color:#dcdcdc;
    font-weight: 500;
}
</style>