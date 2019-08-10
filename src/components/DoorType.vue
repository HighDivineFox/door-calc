<template>
    <div class="section">
        <label for="door-type">Door Type</label>
        <br/>
        <select name="door-type" id="door-type" class="select-style" v-model="doorType">
            <option value="Rear">Rear door</option>
            <option value="Side">Side door</option>
        </select>
        <select name="num" id="num" class="select-style" v-model="numOfDoors">
            <option v-for="i in 2" :key="i" :value="startingDoorNum+i">{{startingDoorNum+i}}</option>
        </select>
    </div>
</template>

<script>

/////
/// The amount to remove from the width is equal to 15 + (15 * the number of doors)
/// The height is always 30mm
/////

/////
/// Rear door can only be 2 or 3
/// Side door can only be 1 or 2
///
/// Polyall hinge only applies to side doors
/////
export default {
    data(){
        return{
            doorType: this.type,
            numOfDoors: this.num
        }
    },
    props:{
        type: String,
        num: Number
    },
    watch: {
        doorType(newVal){
            this.$emit('handleDoorTypeChange', newVal)
        },

        numOfDoors(newVal){
            this.$emit('handleDoorNumChange', Number(newVal))
        },

        num(newVal){
            this.numOfDoors = newVal
        }
    },
    computed: {
        startingDoorNum: function() {
            return this.doorType == "Rear" ? 1 : 0
        }
    }
}
</script>

<style scoped>
    .select-style{
        width: 80%;
        min-width: 200px;
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

    select{
        margin: 5px;
    }

    label{
        font-weight: bold;
    }
</style>
