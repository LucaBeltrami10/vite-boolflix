<template>
    <input type="text" v-model="lookedFor">
    <button @click="$emit('moviesearched', lookedFor)"> Cerca! </button>
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