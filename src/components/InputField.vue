<template>
    <input v-model="value" name="my-input"/>
</template>
<script>
export default {
    props:['default'],
        mounted() {
            this.value = this.default
        },
        updated() {
            return (this.value === this.default) 
                ? this.$emit('dirty-field', false)
                : this.$emit('dirty-field', true);
        },
    data: (()=>{
        return {
            value: ''
        }
    })
}
</script>