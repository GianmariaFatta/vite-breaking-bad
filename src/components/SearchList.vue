<script>
export default {
    name: 'SearchList',
    data() {
        return {
            value: ""
        }
    },
    emits: ['value-change'],
    props: {

        options: Array
    }

}
</script>

<template>
    <select class="form-select" v-model="value" @change="$emit('value-change', value)">
        <option selected value="">All</option>
        <option v-for="option in options" :value=option>{{ option }}</option>

    </select>

</template>

<style scoped>

</style>