<template>
    <div class="element">

        <h2 class="title">{{ movieElement.title }}</h2>
        <h2 class="originalTitle">{{ movieElement.original_title }}</h2>
        
        <img 
            v-if="movieElement.original_language == 'en'" 
            src="../assets/images/en.png" 
            alt="english flag">
        <img 
            v-else-if="movieElement.original_language == 'it'" 
            src="../assets/images/it.png" 
            alt="bandiera italiana">
        <h2 
            class="language" 
            v-else> {{ movieElement.original_language }} 
        </h2>
        <h2 class="vote">{{ movieElement.vote_average }}</h2>

    </div>
</template>

<script>

export default {
    name: "MovieElement",
    props: {
        "movieElement": Object,
    }
}
</script>

<style lang="scss" scope>

    .element {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        width: 19%;
        height: 150px;
        margin: 5px;
        padding: 10px;
        border: 1px solid white;
        font-size: 10px;

        img {
            width: 50px;
        }

        h2 {
            width: 100%;
        }
    }
</style>