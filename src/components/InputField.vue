<template>
    <input v-model="value" name="my-input"/>
</template>
<script>
import EventBus from '../bus';

export default {
    props:['default'],
        mounted() {
            this.value = this.default
        },
        updated() {
            return (this.value === this.default || this.value.length === 0  ) 
                ? EventBus.$emit('dirty-field', false)
                : EventBus.$emit('dirty-field', true);
        },
    data: (()=>{
        return {
            value: ''
        }
    })
}
</script>