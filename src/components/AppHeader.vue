<template>
    <header>
        <input type="text" v-model="lookedFor" @keyup.enter="$emit('movieSearched', lookedFor)">
        <button @click="$emit('movieSearched', lookedFor)"> Cerca! </button>
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

}
</style>