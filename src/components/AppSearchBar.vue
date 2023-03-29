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

        <select name="type" id="card-type" v-model="store.cardType">
            <option value="" disabled selected>Search for card type</option>
            <option value="Effect Monster">Effect Monster</option>
            <option value="Flip Effect Monster">Flip Effect Monster</option>
            <option value="Flip Tuner Effect Monster">Flip Tuner Effect Monster</option>
            <option value="Gemini Monster">Gemini Monster</option>
            <option value="Normal Monster">Normal Monster</option>
            <option value="Normal Tuner Monster">Normal Tuner Monster</option>
            <option value="Pendulum Effect Monster">Pendulum Effect Monster</option>
            <option value="Pendulum Effect Ritual Monster">Pendulum Effect Ritual Monster</option>
            <option value="Pendulum Flip Effect Monster">Pendulum Flip Effect Monster</option>
            <option value="Pendulum Normal Monster">Pendulum Normal Monster</option>
            <option value="Pendulum Tuner Effect Monster">Pendulum Tuner Effect Monster</option>
            <option value="Ritual Effect Monster">Ritual Effect Monster</option>
            <option value="Ritual Monster">Ritual Monster</option>
            <option value="Spell Card">Spell Card</option>
            <option value="Spirit Monster">Spirit Monster</option>
            <option value="Toon Monster">Toon Monster</option>
            <option value="Trap Card">Trap Card</option>
            <option value="Tuner Monster">Tuner Monster</option>
            <option value="Union Effect Monster">Union Effect Monster</option>
        </select>

        <button @click="$emit('searchCardName')">Search</button>

    </div>
    
</template>

<style scoped lang="scss">

    @use './style/mixins.scss' as *;

    .container {
        @include containerCenter();

        input, select {
            margin-right: .3rem;
            padding: .2rem;
            border: none;
            border-radius: 3px;
        }

        input {
            min-width: 250px;
        }

        select {
            background-color: #e0d3c7;
        }

        button {
            padding: .2rem .7rem;
            border: none;
            border-radius: 3px;
            background-color: #e3b081;

        }
    }

</style>