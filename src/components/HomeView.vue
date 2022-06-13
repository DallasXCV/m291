<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <ItemList title="Item Liste" />
    </div>
</template>
<script>
    // @ is an alias to /src
    import ItemList from "@/components/ItemList.vue";
    export default {
        name: "HomeView",
        components: {
            ItemList,
        },
    };
</script>