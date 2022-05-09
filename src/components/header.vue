<template>
<header>
    <input type="text"  v-model="searchedAlbum" @keyup="findAlbum()">
</header>
</template>


<script>
export default {
    name: 'AppHeader',
    methods:{
        findAlbum(){
            console.log('trovalo', this.searchedAlbum)
        }
    }
}


</script>

<style scoped lang="scss">
header{
    background-color: #2E3A46;

    input{
        background-color: #2E3A46;
        width: 100%;
        height: 60px;
        border: 0;
    }
}
</style>
