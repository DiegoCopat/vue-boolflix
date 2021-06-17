<template>
    <div class="element">

        <h2 class="title">{{ seriesElement.name }}</h2>
        <h2 class="originalTitle">{{ seriesElement.original_name }}</h2>
    
        <img 
        v-if="seriesElement.original_language == 'en'" 
        src="../assets/images/en.png" 
        alt="english flag">
        <img 
        v-else-if="seriesElement.original_language == 'it'" 
        src="../assets/images/it.png" 
        alt="bandiera italiana">
        <h2 
        class="language" 
        v-else> {{ seriesElement.original_language }} 
        </h2>
        <h2 class="vote">{{ seriesElement.vote_average }}</h2>
        
    </div>

</template>

<script>

export default {
    name: "SeriesElement",
    props: {
        "seriesElement": Object,
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