<template>
    <div>{{ axiosResponse }}</div>
</template>

<script>
export default {
    props: {
        lookedFor: String,
        axiosResponse: Array,
    }

}
</script>

<style lang="scss" scoped></style>