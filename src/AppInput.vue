<template>
    <div class="form-control" :class="{invalid: error}">
        <label :for="id">Как тебя зовут?</label>
        <input
            :placeholder="placeholder"
            type="text"
            :id="id"
            @input="change"
            :value="modelValue"
        >
        <small v-if="error" >{{ error }}</small>

        <!-- <input
        type="text"
        id="name"
        placeholder="Введи имя"
        ref="nameInput"> -->
    </div>
</template>
<script>
export default {
    
    props:{
        modelValue: String,
        placeholder:String,
        label:String,
        error:{
            type: String
        }
    },
    emits: ['update:modelValue'],
    methods:{
         change(event){
            this.$emit('update:modelValue', event.target.value)
         }
    },
    data(){
        return {
            id: 'input-' + Math.random()
        }
    }
}
</script>