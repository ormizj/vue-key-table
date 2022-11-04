<script setup>
import Vue from 'vue'
</script>


<template>
    <div>
        <h1>KeyTable</h1>
        <div v-for="value in map" :key="value.id">
            {{ value.name }}
            &nbsp;&nbsp;&nbsp;
            <button @click="removeValue(value.id)">Remove Data</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            map: {}
        }
    },

    created() {
        console.log('KeyTable CREATED');
        this.initData();
    },

    updated() {
        console.log('KeyTable UPDATED');
    },

    methods: {
        makeId(length) {
            let result = '';
            let characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
            let charactersLength = characters.length;
            for (var i = 0; i < length; i++) {
                result += characters.charAt(Math.floor(Math.random() * charactersLength));
            }
            return result;
        },

        removeValue(id) {
            Vue.delete(this.map, id);
        },

        initData() {
            const map = {};
            let i = 0;

            while (i++ < 5) {
                const id = this.makeId(100);

                map[id] = {
                    id: id,
                    name: `Data#${i}`
                }
            }

            this.map = map;
        }
    }
}
</script>

<style>

</style>