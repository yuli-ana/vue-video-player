<template>
    <div>
        <input @input="onInput" type="text">
    </div>
</template>

<script>
export default {
    name: "SearchBar",
    methods: {
        onInput: function(e){
            this.$emit('termChange', e.target.value)
        }
   }
};
</script>

<style scoped>
input {
    width: 75%;
    border: 2px solid #000;
}

div{
    text-align: center;
    margin: 20px;
}
</style>