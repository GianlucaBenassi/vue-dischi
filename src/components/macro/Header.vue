<template>
    <header>
        <img src="../../assets/img/logo.png" alt="Spotify logo">
    </header>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style lang="scss" scoped>

header {
    background-color: #2e3a46;
    height: 80px;
    line-height: 80px;

    img {
        height: 80%;
        vertical-align: middle;
        margin-left: 20px;
    }
}

</style>