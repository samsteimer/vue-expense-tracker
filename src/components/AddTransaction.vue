<template>
    <h3>Add new transaction</h3>
    <div class="container border">
        <form @submit.prevent="onSubmit">
            <div class="input-group m-2">
                <label for="text">Text</label>
                <input type="text" class="form-control" id="text" v-model="text" placeholder="Enter text..." />
            </div>
            <div class="input-group mb-3">
                <label for="amount" class="form-label">Amount</label>
                <span class="input-group-text">$</span>
                <input type="text" class="form-control" id="amount" aria-describedby="amountHelp" v-model="amount" placeholder="Enter amount...">
                <small id="amountHelp" class="form-text text-muted">(negative - expense, positive - income)</small>
            </div>
            <div class="input-group mb-3">
                <button class="btn btn-outline-primary">Add transaction</button>
            </div>
        </form>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification';

const text = ref('');
const amount = ref('');

const emit = defineEmits(['transactionSubmitted'])

const toast = useToast();

    const onSubmit = () => {
        if(!text.value || !amount.value) {
            toast.error('Both fields must be filled');
            return;
        }

        const transactionData = {
            text: text.value,
            amount: parseFloat(amount.value)
        }

        emit('transactionSubmitted', transactionData)

        text.value = '';
        amount.value = '';
    };


</script>