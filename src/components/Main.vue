<template>
    <main>
        
        <section class="wrapper">
            <div class="searchBar">
                <input 
                    v-model="searchName" 
                    type="text" 
                    placeholder="Cerca"
                    @keyup.enter="sendSearchName">
                    
                <button
                    @click="sendSearchName"
                    >Invia</button>
                    
            </div>

            <h2>Film</h2>
            <MovieElement 
                
                v-for="movieElement in moviesSearched" :key="movieElement.id"
                :movieElement="movieElement" />

            <h2>Serie TV</h2>
            <SeriesElement 
                
                v-for="seriesElement in seriesSearched" :key="seriesElement.id"
                :seriesElement="seriesElement" />
        </section>

    </main>
</template>

<script>
import MovieElement from "./MovieElement";
import SeriesElement from "./SeriesElement";
import axios from "axios";

export default {
    name: "Main",
    data: function() {
        return {
            searchName: "",
            Api: "https://api.themoviedb.org/3/",
            apiKey: "a9c16860fa33923f90ce639128446c35",
            moviesSearched: [],
            seriesSearched: []
        }
    },
    methods: {
        sendSearchName: function() {

            const constParams = {
                params: {
                        api_key: this.apiKey,
                        query: this.searchName,
                        language: "it-IT"
                }
            };
            
            console.log(this.searchName);
            axios
                .get(this.Api + "search/movie", constParams)
                .then(
                    (response) => {
                        console.log(response);
                        this.moviesSearched = response.data.results;
                        console.log(this.moviesSearched);
                    }
                    
                )
                .catch(
                    (error) => {
                        console.log(error);
                    }
                );
            axios
                .get(this.Api + "search/tv", constParams)
                .then(
                    (response) => {
                        console.log(response);
                        this.seriesSearched = response.data.results;
                        console.log(this.seriesSearched);
                    }
                    
                )
                .catch(
                    (error) => {
                        console.log(error);
                    }
                );
        }
    },
    components: {
        MovieElement,
        SeriesElement
    }
    
}
</script>

<style lang="scss">
@import "../style/General";

    main {
        display: flex;
        width: 100%; 
        // height: calc(100vh - 100px);
        overflow: auto;
        background-color: $bg-light;

        .wrapper {
            display: flex;
            flex-wrap: wrap;
            width: 80%;
            height: 90%;
            margin: 30px auto 30px auto;
            padding: 30px;
            align-content: space-around;
            background-color: $bg-dark;

        & > h2 {
            width: 100%;
            padding: 50px;
        }  

            .searchBar {
                display: flex;
                width: 100%; 
                height: 30px;
                text-align: right;

                input, 
                button {
                    padding: 5px;
                }
            }

        }
        

    }

</style>