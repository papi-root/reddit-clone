<template>
    <Head title="Communities" />
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">Create Community</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="max-w-md mx-auto bg-slate-100 m-2 p-2">
                    <form @submit.prevent="submit">
                        <div>
                            <InputLabel for="name" value="Name" />

                            <TextInput
                                id="name"
                                type="text"
                                class="mt-1 block w-full"
                                v-model="form.name"
                                
                                autofocus
                                autocomplete="name"
                            />

                            <InputError class="mt-2" :message="form.errors.name" />
                        </div>

                        <div>
                            <InputLabel for="description" value="Description" />

                            <TextInput
                                id="description"
                                type="text"
                                class="mt-1 block w-full"
                                v-model="form.description"
                                
                                autofocus
                                autocomplete="description"
                            />

                            <InputError class="mt-2" :message="form.errors.description" />
                        </div>
                        
                        <div>
                            <InputLabel for="slug" value="Slug" />

                            <TextInput
                                id="slug"
                                type="text"
                                class="mt-1 block w-full"
                                v-model="form.slug"
                                
                                autofocus
                                autocomplete="slug"
                            />

                            <InputError class="mt-2" :message="form.errors.slug" />
                        </div>
                

                        <div class="flex items-center justify-end mt-4">
                            <PrimaryButton class="ms-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                                Register
                            </PrimaryButton>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

<script setup>
    import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
    import InputError from '@/Components/InputError.vue';
    import InputLabel from '@/Components/InputLabel.vue';
    import PrimaryButton from '@/Components/PrimaryButton.vue';
    import TextInput from '@/Components/TextInput.vue';
    import { Head, Link, useForm } from '@inertiajs/vue3';

    defineProps({
        errors: Object
    }); 

    const form = useForm({
        name: "",
        description: "",
        slug: "",
    })

    const submit = () => {
        form.post(route('communities.store'));
    };
</script>