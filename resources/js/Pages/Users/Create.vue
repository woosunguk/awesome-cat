<template>
    <app-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                form goes here
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <div class="containers">
                        <div v-if="Object.keys(errors).length > 0" class="alert alert-danger mt-4">
                            {{ errors[Object.keys(errors)[0]][0] }}
                        </div>
                        <form action="/users" method="POST" class="m-5" @submit.prevent="createUser">
                            <div class="form-group">
                                <label for="name">Name</label>
                                <input type="text" class="form-control" id="name" placeholder="Name" v-model="form.name">
                            </div>
                            <div class="form-group">
                                <label for="email">Email</label>
                                <input type="text" class="form-control" id="email" placeholder="Email" v-model="form.email">
                            </div>
                            <div class="form-group">
                                <label for="password">Password</label>
                                <input type="password" class="form-control" id="password" placeholder="Password" v-model="form.password">
                            </div>
                            <button type="submit" class="btn btn-primary">Create User</button>
                        </form>

                    </div>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from './../../Layouts/AppLayout.vue'

    export default {
        props: ['errors'],

        components: {
            AppLayout
        },

        data() {
            return {
                form: {
                    'name': '',
                    'email': '',
                    'password': '',
                }
            }
        },
        methods: {
            createUser() {
                this.$inertia.post('/users', this.form)
                    .then(() => {

                    })
            }
        }
    }
</script>
