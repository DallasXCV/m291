<template>
    <div class="hello">
        <h1>{{ title }}</h1>
        <ul>
            <li v-for="(item, index) in items" :key="index" :data-index="index">
                {{ item.name }}
                <button @click="deleteItem">delete</button>
            </li>
        </ul>
        <label>Name:<input type="text" v-model="newItem.name"></label>
        <br>
        <label>Augen:<input type="text" v-model="newItem.augen"></label>
        <br>
        <button @click="addItem">Neu!</button>
        <br>
        <button @click="saveItem">Speichern!</button>
        <br>
        <button @click="loadItem">Laden!</button>
    </div>
</template>

<script>
    export default {
        name: 'ItemList',
        props: {
            titel: String,
        },
        data() {
            return {
                items: [
                    { name: 'edo', augen: 'grün'},
                    {name: 'joki', augen: 'grau'}
                ],
                newItem: {name:'', augen:''}
            }
        },
        methods: {

            deleteItem(e) {
                const index = e.target.parentElement.database.index;
                this.items.splice(index,1);
            },
            addItem(){
                this.items.push(this.newItem)
            },
            saveItems(){
                localStorage.setItem('items', JSON.stringify(this.items));
            },
            loadItems() {
                if( localStorage.getItem('items'))
                    this.items = JSON.parse(localStorage.getItem('items'));
            },
        },
    };
</script>

<!-- Add "scoped" attribute to limit CSS to this compnent only -->
<style scoped>
    h3{
        margin: 40px 0 0;
    }
    ul{
        list-style-type: none;
        padding: 0;
    }
    li{
        display: inline-block;
        margin: 0 10px;
    }
    a{
        color: #42b983;
    }
</style>