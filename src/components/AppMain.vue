<script>
import {store} from "../store.js";
import axios from "axios";
import AppCard from "../components/AppCard.vue";
import AppSearchBar from './AppSearchBar.vue'

export default {
    data() {
        return {
        store
        }
    },
    
    components: {
        AppCard,
        AppSearchBar
    },

    created() {
        
        axios.get(this.store.APIcall).then((res)=>{
            console.log(res.data.data)
            this.store.cards = res.data.data;
        });
    },

    methods: {
        fetchCard() {

            let apiNewString = this.store.APIcall + '&fname=' + this.store.cardName;

            console.log(apiNewString);
            axios.get(apiNewString).then((res) => {
                console.log(res.data.data);
                this.store.cards = res.data.data;
            });
            
        }
    }
}


</script>

<template>
    <main>
        <h1>Yu-Gi-Oh! Cards</h1>

        <AppSearchBar @searchCardName="fetchCard()"></AppSearchBar>

        <div class="cards-container">            
            <AppCard v-for="card in store.cards" :img="card.card_images[0].image_url" :title="card.name" :type="card.archetype"></AppCard>
        </div>

        <!-- <div v-else class="loading">
            Cards loading...
        </div> -->
    </main>
</template>

<style scoped lang="scss">

    @use './style/mixins.scss' as *;

    main {

        background-image: url('https://mcdn.wallpapersafari.com/medium/34/62/h0VwZu.jpg');
        background-size: cover;
        background-attachment: fixed;

        color: white;
        height: 100vh;
        overflow-y: scroll;
        
        .loading {
            text-align: center;
            font-size: larger;
        }

        h1 {
            padding: 2rem 0;
            text-align:center;
        }

        .cards-container {
            @include containerCenter();
    
            display: flex;
            flex-flow: row wrap;
            gap: 30px;

            padding-bottom: 2rem;
        }
    }

</style>