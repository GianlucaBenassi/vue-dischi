<template>
    <main>
        <div class="container">
            <div class="row">
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

</style>