<script setup>
    // import { useForm } from '@inertiajs/vue3';
    import { router } from '@inertiajs/vue3';

    defineProps({
        customers: Object
    });

    // const form = useForm({
    //     name: null,
    //     email: null,
    //     phone: null
    // });

    function edit(id) {
        router.get(`/customers/${id}/edit`);
    }

    function destroy(id) {
        router.delete(`/customers/${id}`);
    }
</script>

<template>
    <div class="container py-5">
        <div class="alert alert-success" v-if="$page.props.flash.message">
            {{ $page.props.flash.message }}
        </div>
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
                        <button @click="edit(customer.id)" class="btn btn-info shadow-none me-2">Edit</button>
                        <button @click="destroy(customer.id)" class="btn btn-danger shadow-none">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

