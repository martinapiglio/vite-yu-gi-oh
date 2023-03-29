<script>
import {store} from "../store.js";
import axios from "axios";
import AppCard from "../components/AppCard.vue";
import AppSearchBar from './AppSearchBar.vue'
import AppGenerator from './AppGenerator.vue';

export default {
    data() {
        return {
        store
        }
    },
    
    components: {
        AppCard,
        AppSearchBar,
        AppGenerator
    },

    created() {
        
        axios.get(this.store.APIcall).then((res)=>{
            console.log(res.data.data)
            this.store.cards = res.data.data;
            this.store.generatedCardNum = this.store.cards.length;
        });
    },

    methods: {
        fetchCard() {

            let apiNewString = this.store.APIcall;  

            if (this.store.cardName!= '' && this.store.cardType!= '') {
                
                apiNewString = this.store.APIcall + '&fname=' + this.store.cardName + '&type=' + this.store.cardType;
            
            } else if(this.store.cardName!= '' && this.store.cardType == ''){
                
                apiNewString = this.store.APIcall + '&fname=' + this.store.cardName;
            
            } else if(this.store.cardName == '' && this.store.cardType!= ''){
                
                apiNewString = this.store.APIcall + '&type=' + this.store.cardType;

            }

            console.log(apiNewString);

            axios.get(apiNewString).then((res) => {
                console.log(res.data.data);
                this.store.cards = res.data.data;
                this.store.cardName = '';
                this.store.generatedCardNum = this.store.cards.length;
            }).catch((error) => {
                    console.log(error);
                    this.store.cardName = '';
                    alert("No card has been found, please try again with another one!");
                });
            
        }
    }
}

</script>

<template>
    <main>
        <h1>Yu-Gi-Oh! Cards</h1>

        <AppSearchBar @searchCardName="fetchCard()"></AppSearchBar>

        <AppGenerator></AppGenerator>

        <div v-if="store.cards.length> 0" class="cards-container">            
            <AppCard v-for="card in store.cards" :img="card.card_images[0].image_url" :title="card.name" :type="card.archetype"></AppCard>
        </div>

        <div v-else class="loading">
            Cards loading...
        </div> 
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