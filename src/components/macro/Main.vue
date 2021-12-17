<template>
    <main>
        <div class="container">
            <Loader v-if="disks == null"/>
            <div class="disk-list" v-else>
                <div class="row filter">
                    <SelectFilter :infos="disksFiltered" type="genre" @filterSelection="searchGenre"/>
                    <SelectFilter :infos="disksFiltered" type="author" @filterSelection="searchAuthor"/>
                </div>
                <div class="row disks">
                    <DiskCard v-for="(disk, index) in disksFiltered" :key="index" :info="disk"/>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import DiskCard from '../parts/DiskCard.vue';
import Loader from '../parts/Loader.vue';
import SelectFilter from '../parts/SelectFilter.vue'


export default {
    name: 'Header',
    components: {
        DiskCard,
        Loader,
        SelectFilter
    },
    data() {
        return {
            disks: null,
            genreFilter: '',
            authorFilter: ''
        }
    },
    methods: {
        searchGenre(searchText) {
            this.genreFilter = searchText;
        },
        searchAuthor(searchText) {
            this.authorFilter = searchText;
        }
    },
    computed: {
        disksFiltered() {
            return this.disks.filter((elm) => {
                if (elm.genre.includes(this.genreFilter) && elm.author.includes(this.authorFilter)) {
                    return true;
                }
            });
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

.disk-list {

    .filter {
        justify-content: center;
        padding: 20px 0;
    }

    .disks > * {
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
}

</style>