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
    }

</style>