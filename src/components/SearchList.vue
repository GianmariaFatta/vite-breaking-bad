<script>
import { store } from '../data/store';
export default {
    name: 'SearchList',
    data() {
        return {
            store,
            value: ""
        }
    },
    emits: ['value-change'],
}
</script>

<template>
    <select class="form-select" v-model="value" @change="$emit('value-change', value)">
        <option selected>Open this select menu</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
    </select>

</template>

<style scoped>

</style>