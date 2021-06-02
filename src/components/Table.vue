<template>
    <table class="table" v-if="show">
        <tr class="table__row">
            <th class="table__header">Спринт</th>
            <th class="table__header">Кайзер</th>
            <th class="table__header">неКайзер</th>
        </tr>
        <tr v-for="(item, idx) in items" :key="idx" class="table__row">
            <td class="table__cell">{{ idx }}</td>
            <td class="table__cell">{{ item.kaiser }}</td>
            <td class="table__cell">{{ item.notKaiser }}</td>
        </tr>
    </table>
</template>

<script>
import { stat } from '@/data.js';

export default {
    name: 'Table',
    props: {
        show: {
            type: Boolean,
            default: false,
        },
    },
    data() {
        return {
            items: stat,
        };
    },
};
</script>

<style>
.table {
    border-collapse: collapse;
}

.table__header,
.table__cell {
    border: grey 1px solid;
}

.table__header {
    background: lightgray;
    width: 200px;
}
</style>
