<template>
    <div class="list">
        <div v-for="(item, index) in items" :key="index">
            <router-link :to="{name: 'items', params: {id: index}}" tag="div">
                <img :src="item.image">
                <h4>
                    <span>{{item.title}} - {{item.price}}$</span>
                </h4>
            </router-link>
                <AddToCart :index="index"/>
        </div>
    </div>
</template>

<script>

    import AddToCart from "./AddToCart";

    export default {
        name: 'Home',
        components: {
            AddToCart
        },
        computed: {
            items: function () {
                return this.$store.state.items
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .list {
        display: flex;
        flex-direction: row;
        justify-items: center;
    }

    .list > div {
        margin: 20px;
        padding: 20px;
        text-align: center;
        flex: 1 1 0px;
        background-color: #ffffff;
        border-radius: 4px;
        box-shadow: 2px 2px 4px 0px #a5a5a5;;
    }

    .list > div img {
        height: 100px;
    }

    .list > div span {
        color: #1a1a1a;
        text-decoration: none;
    }

    .list > div span:hover {
        color: #ff5f52;
        text-decoration: underline;
    }
</style>
