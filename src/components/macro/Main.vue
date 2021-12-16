<template>
    <main>
        <div class="container">
            <div class="disk-list row">
                <DiskCard v-for="(disk, index) in disks" :key="index" :info="disk"/>
            </div>
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import DiskCard from '../parts/DiskCard.vue';


export default {
    name: 'Header',
    components: {
        DiskCard
    },
    data() {
        return {
            disks: null
        }
    },
    created() {
        // get disks array
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            // handle success
            this.disks = response.data.response;
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
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
    margin: 10px 20px;

    @media screen and (min-width: 576px) {
        width: calc(100% / 2 - 40px);
    }

    @media screen and (min-width: 768px) {
        width: calc(100% / 3 - 40px);
    }

    @media screen and (min-width: 992px) {
        width: calc(100% / 5 - 40px);
    }
}

</style>