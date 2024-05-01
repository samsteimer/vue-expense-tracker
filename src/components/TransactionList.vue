<template>
    <div class="container rounded border border-2 mb-1">
        <h3>History</h3>
        <ul id="list" class="list-group mb-1">
            <li class="list-group-item position-relative d-flex justify-content-between align-items-center" v-for="transaction in transactions" v-bind:key="transaction.id" :class="transaction.amount < 0 ? 'list-group-item-danger' : 'list-group-item-success'">
                <span class="me-auto">{{ transaction.text }} <span>${{ transaction.amount }}</span></span>
                <button @click="deleteTransaction(transaction.id)" class="btn btn-danger btn-sm position-abolute start-100">delete</button>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const emit = defineEmits(['transactionDeleted'])

const props = defineProps({
    transactions: {
        type: Array,
        required: true
    }
});

const deleteTransaction = (id) => {
    emit('transactionDeleted', id);
}   

</script>

