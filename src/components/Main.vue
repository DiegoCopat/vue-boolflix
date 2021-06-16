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

            <Element />
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
            searchName: ""
        }
    },
    methods: {
        sendSerchName: function() {
            
        }
    },
    components: {
        Element
    },
    created: function() {
        axios
            .get("https://api.themoviedb.org/3/movie/550?api_key=a9c16860fa33923f90ce639128446c35")
            .then()
            .catch();
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