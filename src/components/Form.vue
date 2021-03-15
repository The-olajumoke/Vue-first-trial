<template>
    <input type="text" v-model="text" name="text">
    {{text}}
</template>


<script>
export default {
name: 'Form',
data(){
    return{
        text: '',
    }
}
}
</script>