<script>
import {store} from "../store.js";
import axios from "axios";
import AppCard from "../components/AppCard.vue";

export default {
    data() {
        return {
        store
        }
    },
    
    components: {
        AppCard,
    },

    created() {
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=9&offset=0').then((res)=>{
            console.log(res.data.data)
            this.store.cards = res.data.data;
        });
    }
}

</script>

<template>
    <main>
        <h1>Yu-Gi-Oh! Cards</h1>
        <div class="cards-container">
            <AppCard v-for="card in store.cards" :img="card.card_images[0].image_url" :title="card.name" :type="card.archetype">
            </AppCard>
        </div>
    </main>
</template>

<style scoped lang="scss">

    main {

        background-image: url('https://mcdn.wallpapersafari.com/medium/34/62/h0VwZu.jpg');
        background-size: cover;
        background-attachment: fixed;

        color: white;

        h1 {
            padding: 2rem 0;
            text-align:center;
        }

        .cards-container {
            max-width: 900px;
            margin: auto;
    
            display: flex;
            flex-flow: row wrap;
            gap: 30px;

            padding-bottom: 2rem;
        }
    }

</style>