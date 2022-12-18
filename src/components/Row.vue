<template>
    <div class="group-section">
        <img :src="row.val6" alt="image" />
        <p>{{row.val1}}</p>
        <p>{{row.val2}} kg</p>
        <p>{{row.val4 + row.val5}}</p>
        <p>{{row.val7}}</p>
        <p>{{row.val8}}</p>
    </div>
</template>

<script>
export default{
    name: "Row",
    props: {
        row: Object,
    }
}
</script>

<style scoped>
div{
    margin-bottom: 5px;
    padding: 10px 0;
}

div:nth-child(even){
    background: #fff9f9;
}

div:nth-child(odd){
    background: #f7fdfb;
}

img{
    width: 100%;
}
</style>