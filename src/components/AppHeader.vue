<template>
    <input type="text" v-model="lookedFor" @keyup.enter="$emit('moviesearched', lookedFor)">
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