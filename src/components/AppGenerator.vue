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
        <div id="text">Generated cards: {{ this.store.generatedCardNum }}</div>
    </div>
    
</template>

<style scoped lang="scss">

    @use './style/mixins.scss' as *;

    .container {
        @include containerCenter();

        #text {
            padding: 1rem 0;
            font-size: 14px;
        }
    }

</style>