<script setup>
    // import { useForm } from '@inertiajs/vue3';
    // import { router } from '@inertiajs/vue3';

    defineProps({
        customers: Object
    });

    // const form = useForm({
    //     name: null,
    //     email: null,
    //     phone: null
    // });

    // function submit() {
    //     router.post('/customers', form);
    // }
</script>

<template>
    <div class="container py-5">
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="customer in customers">
                    <td>{{ customer.name }}</td>
                    <td>
                        <button class="btn btn-info shadow-none me-2">Edit</button>
                        <button class="btn btn-danger shadow-none">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

