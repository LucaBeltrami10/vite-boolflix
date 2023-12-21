<template>
    <input type="text" v-model="lookedFor" @keyup.enter="$emit('movieSearched', lookedFor)">
    <button @click="$emit('movieSearched', lookedFor)"> Cerca! </button>
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

<style lang="scss" scoped></style>