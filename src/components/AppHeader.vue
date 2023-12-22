<template>
    <header>
        <div class="logo-container">
            <img src="../assets/img/netflix_logo.png" alt="Netflix Logo">
        </div>
        <nav>
            <ul class="d-flex m-0 p-0">
                <li class="mx-2">Serie TV</li>
                <li class="mx-2">Film</li>
                <li class="mx-2">Aggiunti Di Recente</li>
                <li class="mx-2">Preferiti</li>
            </ul>
            <ul class="d-flex  m-0 me-3 p-0">
                <input type="text" v-model="lookedFor" @keyup.enter="$emit('movieSearched', lookedFor)">
                <button @click="$emit('movieSearched', lookedFor)"> Cerca! </button>
            </ul>

        </nav>

    </header>
</template>

<script>
export default {
    data() {
        return {
            lookedFor: '',

        }
    }
}
</script>

<style lang="scss" scoped>
@use '../style/partials/variables' as *;
@use '../style/partials/mixins' as *;

header {
    height: 15vh;
    background-color: $bg-header;

    @include flex(row, start, center);

    div.logo-container {
        width: 15%;

        img {
            width: calc(100% - 1.8rem);
            margin: 0 0.9rem 0 0.9rem;
        }
    }

    nav {
        @include flex(row, space-between, center);
        width: 85%;
        height: 100%;
        color: white;
    }

}
</style>