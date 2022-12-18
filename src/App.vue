<template>
    <div>
        <Header />
        <Rows :rows="generateTable()" />
    </div>
</template>

<script>
import Header from "./components/Header.vue";
import Rows from "./components/Rows.vue";

export default {
    name: "App",
    components: {
        Header,
        Rows,
    },
    data() {
        return {
            rowsCount: 100,
            rows: [],
            array: ["str1", "str2", "str3", "str4", "str5"],
        };
    },
    methods: {
        generateTable(){
            for(let i = 0; i < this.rowsCount; i++){
                this.rows.push({
                    val1: this.getRandString(10),
                    val2: this.getRandFloat(10, 2),
                    val3: this.getRandFloat(10, 4),
                    val4: this.getRandInteger(20),
                    val5: this.getRandInteger(10),
                    val6: this.getRandImage(),
                    val7: this.getRandString(10),
                    val8: this.getString(),
                });
            }
            return this.rows;
        },
        getRandString(length){
            let result = "";
            const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz';
            for (let i = 0; i < length; i++) {
                result += characters.charAt(Math.floor(Math.random() * characters.length));
            }
            return result.charAt(0).toUpperCase() + result.slice(1).toLowerCase();
        },
        getRandInteger(length){
            return Math.floor(Math.random() * length) + 1;
        },
        getRandFloat(length, decimal){
            return (Math.random() * length).toFixed(decimal);
        },
        getRandImage(){
            return `https://picsum.photos/id/${this.getRandInteger(200)}/200`;
        },
        getString(){
            return this.array[Math.floor(Math.random() * this.array.length)];
        },
    }
}
</script>

<style>
.group-section{
    min-width: 300px;
    display: grid;
    grid-template-columns: repeat(6, 1fr);
}

.group-section > *{
    padding-right: 10px;
}

.group-section--two{
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    border-bottom: 1px solid black;
}
</style>