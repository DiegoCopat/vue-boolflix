<template>
    <main>
        
        <section class="wrapper">
            <div class="searchBar">
                <input 
                    v-model="searchName" 
                    type="text" 
                    placeholder="Cerca">
                <button
                    @click="sendSearchName"
                    >Invia</button>
            </div>

            <Element 
                
                v-for="element in moviesSearched" :key="element.id"
                :movieElement="element" />
        </section>

    </main>
</template>

<script>
import Element from "./Element";
import axios from "axios";

export default {
    name: "Main",
    data: function() {
        return {
            searchName: "",
            moviesApi: "https://api.themoviedb.org/3/search/movie",
            apiKey: "a9c16860fa33923f90ce639128446c35",
            moviesSearched: []
        }
    },
    methods: {
        sendSearchName: function() {
            console.log(this.searchName);
            axios
                .get(this.moviesApi, {
                    params: {
                        api_key: this.apiKey,
                        query: this.searchName,
                        language: "it-IT"
                    }
                })
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
        }
    },
    components: {
        Element
    }
    
}
</script>

<style lang="scss">
@import "../style/General";

    main {
        display: flex;
        width: 100%; 
        height: calc(100vh - 100px);
        background-color: $bg-light;

        .wrapper {
            display: flex;
            flex-wrap: wrap;
            width: 80%;
            height: 90%;
            margin: auto;
            align-content: space-around;
            background-color: $bg-dark;

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