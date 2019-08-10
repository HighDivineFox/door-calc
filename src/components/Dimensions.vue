<template>
    <div class="section flex-col">
        <span>Dimensions</span>
        <input class="dimen" type="number" name="Width" id="Width" placeholder="Enter Width" v-model="width" @input="handleWidth">
        <input class="dimen" type="number" name="Height" id="Height" placeholder="Enter Height" v-model="height" @input="handleHeight">
    </div>
</template>

<script>
export default {
    data(){
        return{
            width: this.inputWidth,
            height: this.inputHeight
        }
    },
    props:{
        inputWidth: Number,
        inputHeight: Number
    },
    methods:{
        handleWidth(ev){
            this.$emit('handleWidthChange', Number(ev.target.value))
        },

        handleHeight(ev){
            this.$emit('handleHeightChange', Number(ev.target.value))
        }
    }
}
</script>

<style scoped>
    .dimen{
        width: 75%;
        min-width: 200px;
        
        height: auto;
        font-size: 150%;
        text-align: right;
        padding: 5px;
        margin: 5px;

        border-radius: .2em;
        border: none;
        box-shadow: 0px 0px 2px 2px rgba(0,0,0,0.3);
    }

    .dimen::placeholder{
        color: #DDD;
    }

    span{
        font-size: 120%;
        font-weight: bold;
    }

    .flex-col{
        display: flex;
        flex-flow: column nowrap;
        
        align-items: center;
    }

    label{
        font-weight: bold;
    }

</style>
