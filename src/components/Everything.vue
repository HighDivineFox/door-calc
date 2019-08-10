<template>
    <div>
        <h1>Door Calculator</h1>
        <DoorType />
        <HingeType />
        <Dimension />

        <div class="section">
            <input type="button" value="Calculate" class="calculate">
        </div>
    </div>
</template>

<script>
import DoorType from './DoorType'
import HingeType from './HingeType'
import Dimension from './Dimension'

export default {
    components:{
        DoorType,
        HingeType,
        Dimension
    },
    data(){
        return{

        }
    }
}
</script>

<style scoped>
    .calculate{
        font-size: 150%;
        padding: 5px;
        border-radius: 5px;
    }
</style>
