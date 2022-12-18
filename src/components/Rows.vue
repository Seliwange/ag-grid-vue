<template>
    <section>
        <div class="select-group">
            <div class="sum-col3">
                Sum: {{sumRows}}
            </div>
            <div class="sum-col4">
                Average: {{averageRows}}
            </div>
            <select id="filter" v-model="filter">
                <option :value="filter" v-for="(filter, index) in filters" :key="index">
                    {{ filter }}
                </option>
            </select>
        </div>
        <div>
            <Row v-for="(row, index) in filteredRows"
            :key="index" :row="row" @click="getRow(row)" />
            <div v-if="filteredRows.length === 0">No data</div>
        </div>
    </section>
</template>

<script>
import Row from "./Row.vue";

export default {
    name: "Rows",
    components: {
        Row,
    }, 
    props: ["rows"],
    data() {
        return{
            filter: "All",
            filters: ["All", "str1", "str2", "str3", "str4", "str5"],
        }
    },
    computed: {
        filteredRows() {
            if(this.filter === "All") {
                return this.rows;
            }
            return this.rows.filter(row => row.val8 === filter.value);
        },
        sumRows() {
            return this.filteredRows.reduce((acc, row) => acc + +row.val2, 0).toFixed(2);
        },
        averageRows() {
            if(this.filteredRows.length === 0) return 0;
            return Math.floor(this.filteredRows.reduce((acc, row) => (acc + (row.val4 + row.val5)), 0) / this.filteredRows.length);
        }
    },
    methods: {
        getRow(row) {
            alert(`You have next data in this row: image, ${row.val1}, ${row.val2}, ${row.val4 + row.val5}, ${row.val7}, ${row.val8}`);
        }
    }
}
</script>

<style scoped>
.select-group{
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    justify-items: end;
    position: relative;
    background-color: lightgray;
}
.select-group::after {
    content: "";
    position: absolute;
    right: 5px;
    top: calc(80%/2);
    justify-self: end;
    width: 12px;
    height: 8px;
    background-color: #ababab;
    clip-path: polygon(100% 0%, 0 0%, 50% 100%);
}

.sum-col3{
    grid-column: 3/4;
    justify-self: start;
}
.sum-col4{
    grid-column: 4/5;
    justify-self: start;
}

select{
    width: 100%;
    grid-column: 6/7;
    appearance: none;
    background-color: transparent;
    border: none;
    font-family: inherit;
    font-size: inherit;
    cursor: inherit;
    line-height: inherit;
    z-index: 1;
}

option{
    background-color: #f2f2f2;
    font-family: inherit;
    font-size: inherit;
}
</style>