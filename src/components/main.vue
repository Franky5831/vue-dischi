<template>
<main>
    <div class="card">
        <img src="../../src/assets/logo.png" alt="">
        <h1>title</h1>
        <h2>author</h2>
        <h3>date</h3>
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
            console.log(res)
        })
    }
}
</script>

<style scoped lang="scss">
main{
    height: calc(100vh - 60px);
    background-color: #1E2D3B;
    display: flex;
    justify-content: center;
    align-items: center;

    .card{
        background-color: #2E3A46;
        width: 12.5%;
        min-height: 40%;
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
