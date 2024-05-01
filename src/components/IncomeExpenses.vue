<template>
    <div class="container rounded border border-2 mb-1">
        <div class="text-success">
            <h4>Income</h4>
            <p id="money-plus" class="money plus">$ {{ income }}</p>
        </div>
        <div class="text-danger">
            <h4>Expense</h4>
            <p id="money-minus" class="money minus">$ {{ expenses }}</p>
        </div>
    </div>
</template>

<script setup>
    import {defineProps} from 'vue';

    const props = defineProps({
        income: {
            type: Number,
            required: true
        },
        expenses: {
            type: Number,
            required: true
        },
    })
</script>