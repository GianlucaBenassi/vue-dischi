<template>
    <div class="card">
        <img :src="info.poster" :alt="info.title">
        <h2>{{info.title}}</h2>
        <p>{{info.author}}</p>
        <p>{{info.year}}</p>
    </div>
</template>

<script>
export default {
    name: 'DiskCard',
    props: {
        info: Object
    }
}
</script>

<style lang="scss" scoped>

.card {
    background-color: #2e3a46;
    text-align: center;
    padding: 20px;

    img {
        width: 100%;
    }

    h2 {
        color: #fff;
        text-transform: uppercase;
        margin-top: 10px;
        margin-bottom: 20px;
    }

    p {
        color: #7e7f7d;
    }
}

</style>