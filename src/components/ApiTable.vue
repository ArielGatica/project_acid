<template>
    <el-table :data="items" border style="width: 100%">
        <el-table-column prop="name" label="Nombre" width="180"></el-table-column>
        <el-table-column prop="status" label="Estado" width="180"></el-table-column>
        <el-table-column prop="gender" label="Género"></el-table-column>
        <el-table-column prop="species" label="Género"></el-table-column>
        <el-table-column prop="origin.name" label="Origen"></el-table-column>
    </el-table>
</template>

<script>
    import axios from "axios";

    export default {
    data() {
        return {
        items: [],
        img: []
        };
    },
    beforeMount() {
        async function getDataApi() {
        try {
            const readDataApi = axios.get("https://rickandmortyapi.com/api/character/");
            if (readDataApi) 
                return readDataApi;
        } catch (error) {
            return error;
        }
        }
        getDataApi().then(response => {
            if(response.status == 200)
                this.items = response.data.results
        })
        .catch((error) => { console.log(`Error ${error}`)})
    }
    };
</script>