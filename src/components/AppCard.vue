<script>
import {store} from "../store.js";

export default{
    data(){
        return{
            store
        }
    },
    props:{
        title: String,
        img: String,
        type: String
    }
  }
</script>

<template>
    <div class="card">

        <img :src="img" alt="">

        <div id="title">
           <span>Card Name</span>: {{title}}
        </div>

        <div id="type">
            <span>Card Archetype</span>: {{type}}
        </div>

    </div>
</template>

<style scoped lang="scss">
    .card {
        width: calc(100% / 3 - (30px / 3 * 2));
        font-size: smaller;
        text-align: left;

        img {
            width: 100%;
            margin-bottom: .5rem;
        }

        #title span, #type span {
            font-weight: bold;
            font-size: small;
        }
    }
</style>