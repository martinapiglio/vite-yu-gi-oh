<script>
import {store} from "../store.js";

export default {
    data() {
        return {
            store
        }
    },
}

</script>

<template>

    <div class="container">
        <input @keyup.enter="$emit('searchCardName')" type="text" placeholder="Search for card name" v-model="store.cardName">
        <button @click="$emit('searchCardName')">Search</button>
    </div>
    
</template>

<style scoped lang="scss">

    @use './style/mixins.scss' as *;

    .container {
        @include containerCenter();

        input {
            min-width: 250px;
            margin-right: .3rem;
            padding: .2rem;
            border: none;
            border-radius: 3px;
        }

        button {
            padding: .2rem;
            border: none;
            border-radius: 3px;
            background-color: #e3b081;

        }
    }

</style>