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
        <div>Generated cards: {{ this.store.generatedCardNum }}</div>
    </div>
    
</template>

<style scoped lang="scss">

    @use './style/mixins.scss' as *;

    .container {
        @include containerCenter();
    }

</style>