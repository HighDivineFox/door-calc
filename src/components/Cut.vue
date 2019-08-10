<template>
    <div class="section flex-col">
        <label>Cut panel to:</label>
        <div>Width: {{((this.width - this.calculateTo()) / this.numOfDoors).toFixed(2)}}mm</div>
        <div>Height: {{(this.height - 30).toFixed(2)}}mm</div>        
        <input type="button" value="Back" class="back" @mouseup="$emit('back')">
    </div>
</template>

<script>
export default {
    props: {
        width: Number,
        height: Number,
        numOfDoors: Number,
        hingeType: String
    },
    methods:{
        calculateTo(){
            if(this.hingeType == "Standard"){
                return 15 + (15 * this.numOfDoors)
            } else if(this.hingeType == "Polyall"){
                return 15 + (25 * this.numOfDoors)
            }
        }
    }
}
</script>

<style scoped>

    *{
        font-size: 120%;
        margin-top: 5px;
    }

    .flex-col{
        display: flex;
        flex-flow: column nowrap;

        height: max-content;
        align-items: center;
    }

    label{
        font-weight: bold;
    }

    .back{
        font-size: 150%;
        width: 80%;
        min-width: 300px;
        padding: 10px;
        border-radius: .5em;

        background-image: linear-gradient(180deg, #99F, #66E);
        color: aliceblue;

        min-height: max-content;
    }
</style>
