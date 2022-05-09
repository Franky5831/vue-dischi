<template>
<main>
    <div id="selects">
        <select name="genere" id="selectGenere" v-model="selectedGen">
            <option disabled value="">Filter the genres</option>
            <option value="">All</option>
            <option>Rock</option>
            <option>Pop</option>
            <option>Jazz</option>
            <option>Metal</option>
        </select>

        <select name="artist" id="selectArtist" v-model="selectedArt">
            <option disabled value="">Filter the artists</option>
            <option>Bon Jovi</option>
            <option>Queen</option>
            <option>Sting</option>
            <option>Steve Gadd Band</option>
            <option>Iron Maiden</option>
            <option>Eric Clapton</option>
            <option>Deep Purple</option>
            <option>Metallica</option>
            <option>Dave Weckl</option>
            <option>Michael Jacjson</option>
        </select>
    </div>
    <div id="containerCards">
        <div class="card"
        v-show="(selectedGen === item.genre || selectedGen === '') && (selectedArt === item.author || selectedArt === '')"
        v-for="(item, index) in albums" :key="index.id">
            <img :src="item.poster" alt="">
            <h1>{{item.title}}</h1>
            <h2>{{item.author}}</h2>
            <h3>{{item.year}}</h3>
        </div>

    </div>

</main>
</template>


<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data(){
        return{
            selectedGen: '',
            selectedArt: '',
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
    height: calc(100vh - 100px);
    #selects{
        display: flex;
        justify-content: flex-end;
        gap: 40px;
        padding: 20px;
        select{
            background-color: #2E3A46;
            color: white;
            border-radius: 5px;
            border: 0;
            font-size: 1.3rem;
        }
    }


    #containerCards{
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
            }
            h1{
                color: white;
                font-size: 1.5em;
                margin-bottom: 10px;
                text-transform: uppercase;
            }
            h2, h3{
                color: #807872;
                font-size: 1em;
            }
            h3{
                margin-bottom: 20px;
            }
        }
    }


}

</style>
