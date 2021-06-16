<template>
    <header>
        <h1>Boolflix</h1>
        
  </header>
</template>

<script>
export default {
    name: "Header"

}
</script>

<style lang="scss">
@import "../style/General";

    header {
        display: flex;
        align-content: center;
        height: 100px;
        padding: 30px;
        background-color: $bg-dark;

        h1 {
            margin: auto 0;
        }
    }

</style>