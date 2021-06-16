<template>
    <div class="element">
        <h2 class="title">{{ movieElement.title }}</h2>
        <h2 class="originalTitle">{{ movieElement.original_title }}</h2>
        <h2 class="language">{{ movieElement.original_language }}</h2>
        <h2 class="vote">{{ movieElement.vote_average }}</h2>
    </div>

</template>

<script>

export default {
    name: "Element",
    props: {
        "movieElement": Object
    }
}
</script>

<style lang="scss" scope>

    .element {
        margin: 5px;
        padding: 10px;
        border: 1px solid white;
    }
</style>