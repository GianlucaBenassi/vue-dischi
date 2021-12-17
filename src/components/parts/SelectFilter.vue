<template>
    <div class="filter">

        <label for="sel-filter">{{type}}:</label>

        <select name="sel-filter" v-model="selValue" @change="$emit('filterSelection', selValue)">
            <option value="">All</option>
            <option v-for="(value, index) in arrValues" :key="index" :value="value">{{value}}</option>
        </select>

    </div>
</template>

<script>
export default {
    name: 'SelectFilter',
    props: {
        infos: Array,
        type: String
    },
    data() {
        return {
            arrValues: [],
            selValue: ''
        }
    },
    methods: {
        deleteDuplicates() {
            this.infos.forEach(el => {
                if (!this.arrValues.includes(el[this.type])) {
                    this.arrValues.push(el[this.type]);
                }
            });
        }
    },
    mounted() {
        this.deleteDuplicates();
    },
    watch: {
        infos() {
            this.arrValues = [];
            this.deleteDuplicates();
        }
    }
}
</script>

<style lang="scss" scoped>

.filter {
    text-align: center;
    flex-grow: 1;

    label {
        color: #fff;
        text-transform: uppercase;
        margin-right: 10px;
    }
}


</style>