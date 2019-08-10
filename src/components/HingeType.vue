<template>
    <div class="section flex-col">
        <label for="door-type">Hinge Type</label>
        <select name="door-type" id="door-type" class="select-style" v-model="hingeType">
            <option value="Standard">Standard</option>
            <option v-if="this.doorType != 'Rear'" value="Polyall">Polyall</option>ml
        </select>
    </div>
</template>

<script>

/////
/// Polyall hinges 15 + (25 * the number of doors)
/////

export default {
    data(){
        return{
            hingeType: this.type
        }
    },
    props: {
        type: String,
        doorType: String
    },
    watch:{
        hingeType(newVal){
            this.$emit('handleHingeChange', newVal)
        },

        doorType(){
            if(this.doorType == "Rear" && this.hingeType == "Polyall"){
                this.hingeType = "Standard"
            }
        }
    }
}
</script>

<style scoped>
    .select-style{
        width: 80%;
        min-width: 280px;
        height: auto;

        font-size: 150%;
        font-weight: 500;
        color: #444;
        background-image: linear-gradient(180deg, #FFFFFF, #E5E5E5);
        padding: 5px 15px;

        border: 1px solid #aaa;
        box-shadow: 0 2px 0 2px rgba(0,0,0,0.04);
        border-radius: .5em;
    }

    .flex-col{
        display: flex;
        flex-flow: column nowrap;
        
        align-items: center;
        min-height: max-content;
    }

    label{
        font-weight: bold;
    }
</style>
