<template>
<main >
    <div class="card" v-show="/*this.searchedAlbum.tolowercase() === item.title.tolowercase()*/ true" v-for="(item, index) in albums" :key="index.id">
        <img :src="item.poster" alt="">
        <h1>{{item.title}}</h1>
        <h2>{{item.author}}</h2>
        <h3>{{item.year}}</h3>
    </div>

</main>
</template>


<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data(){
        return{
            albums:[]
        }
    },
    mounted(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((res)=>{
            this.albums = res.data.response
        })
    },
}
</script>

<style scoped lang="scss">
main{
    height: calc(100vh - 60px);
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 2%;
    padding: 0 15%;

    .card{
        background-color: #2E3A46;
        width: 18%;
        text-align: center;

        img{
            width: 80%;
            margin: 10%;
            background-color: red;
        }
        h1{
            color: white;
            font-size: 2em;
            margin-bottom: 10%;
            text-transform: uppercase;
        }
        h2, h3{
            color: #807872;
            font-size: 1.2em;
        }
        h3{
            margin-bottom: 10%;
        }
    }
}

</style>
