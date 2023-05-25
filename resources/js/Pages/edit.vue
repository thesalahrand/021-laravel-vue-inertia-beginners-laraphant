<script setup>
    import { useForm } from '@inertiajs/vue3';
    import { router } from '@inertiajs/vue3';

    const props = defineProps({
        errors: Object,
        customer: Object
    });

    const form = useForm({
        name: props.customer.name,
        email: props.customer.email,
        phone: props.customer.phone
    });

    function submit(id) {
        router.put(`/customers/${id}`, form);
    }
</script>

<template>
    <div class="container py-5">
        <div class="row">
            <div class="col-6 mx-auto">
                <div class="card">
                    <div class="card-header">
                        Edit Customer
                    </div>
                    <div class="card-body">
                        <form @submit.prevent="submit(customer.id)" action="">
                            <div class="mb-3">
                                <label class="form-label" for="name">Name</label>
                                <input type="text" v-model="form.name" class="form-control shadow-none" id="name">
                                <span class="text-danger" v-if="errors.name">{{ errors.name }}</span>
                            </div>
                            <div class="mb-3">
                                <label class="form-label" for="email">Email</label>
                                <input type="email" v-model="form.email" class="form-control shadow-none" id="email">
                                <span class="text-danger" v-if="errors.email">{{ errors.email }}</span>
                            </div>
                            <div class="mb-3">
                                <label class="form-label" for="phone">Phone</label>
                                <input type="tel" v-model="form.phone" class="form-control shadow-none" id="phone">
                                <span class="text-danger" v-if="errors.phone">{{ errors.phone }}</span>
                            </div>
                            <button class="btn btn-primary shadow-none w-100" type="submit">Update</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

