<template>
    <main>
        <div class="container">
            <div class="disk-list row">
                <DiskCard/>
                <DiskCard/>
                <DiskCard/>
                <DiskCard/>
                <DiskCard/>
                <DiskCard/>
                <DiskCard/>
                <DiskCard/>
                <DiskCard/>
                <DiskCard/>
            </div>
        </div>
    </main>
</template>

<script>
import DiskCard from '../parts/DiskCard.vue';

export default {
    name: 'Header',
    components: {
        DiskCard
    }
}
</script>

<style lang="scss" scoped>

main {
    background-color: #1e2d3b;
    min-height: calc(100vh - 80px);
}

.disk-list > * {
    width: 100%;
    margin: 20px 30px;

    @media screen and (min-width: 576px) {
        width: calc(100% / 2 - 60px);
    }

    @media screen and (min-width: 768px) {
        width: calc(100% / 3 - 60px);
    }

    @media screen and (min-width: 992px) {
        width: calc(100% / 5 - 60px);
    }
}

</style>