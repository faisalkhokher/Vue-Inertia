<template>
<Layout>

 <section>
        <div class="flex justify-between">
            <p class="user-create">User's Create</p>
        </div>
    </section>

    <section id="create-section" class="container">
        <form @submit.prevent="save" method="post" action="/">
            <div class="form-group">
                <label for="">Name</label>
                <input type="text" name="name" v-model="form.name" id="" class="border border-gray-400 p-2 w-full" placeholder="" aria-describedby="helpId">
                <small id="helpId"  v-if="errors.name" class="text-red-500">{{errors.name}}</small>
            </div>
            <div class="form-group">
                <label for="">Email</label>
                <input type="email" name="email" v-model="form.email" id="" class="border border-gray-400 p-2 w-full my-1" placeholder="" aria-describedby="helpId">
                <small id="helpId"  v-if="$page.props.errors" class="text-red-500">{{$page.props.errors.email}}</small>
            </div>
            <div class="form-group">
                <label for="">Password</label>
                <input type="text" name="password" v-model="form.password" class="border border-gray-400 p-2 w-full" placeholder="" aria-describedby="helpId">
                <small id="helpId"  v-if="$page.props.errors" class="text-red-500">{{$page.props.errors.password}}</small>
            </div>
            <div>
                <button type="submit" class="bg-blue-400 py-2 px-4 my-2 rounded">Submit</button>
            </div>
        </form>
    </section>


</Layout>

    <!-- <section>
            <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
                <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
                    <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                        <tr>
                            <th scope="col" class="p-4">
                                <div class="flex items-center">
                                    <input id="checkbox-all" type="checkbox" class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                                    <label for="checkbox-all" class="sr-only">checkbox</label>
                                </div>
                            </th>
                            <th scope="col" class="px-6 py-3">
                                User Name
                            </th>
                            <th scope="col" class="px-6 py-3">
                                User Email
                            </th>
                            <th scope="col" class="px-6 py-3">
                                User Date
                            </th>
                            <th scope="col" class="px-6 py-3">
                                <span class="sr-only">Edit</span>
                            </th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr
                         v-for="user in users.data"
                        :key="user.id"
                        class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
                            <td class="w-4 p-4">
                                <div class="flex items-center">
                                    <input id="checkbox-table-1" type="checkbox" class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                                    <label for="checkbox-table-1" class="sr-only">checkbox</label>
                                </div>
                            </td>
                            <th scope="row" class="px-6 py-4 font-medium text-gray-900 dark:text-white whitespace-nowrap">
                                {{ user.name }}
                            </th>
                            <td class="px-6 py-4">
                                {{ user.email }}
                            </td>
                            <td class="px-6 py-4">
                                {{ user.created_at }}
                            </td>
                            <td class="px-6 py-4 text-right">
                                <a href="#" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Edit</a>
                            </td>
                        </tr>

                    </tbody>
                </table>
            </div>

        </section> -->
    <!-- <Pagination :links="users.links">
        </Pagination> -->
</template>

<script setup>
import Pagination from '../shared/Pagination'
import Layout from '../shared/Layout';
import { Inertia } from '@inertiajs/inertia'
import { watch, ref } from 'vue';
import { reactive } from 'vue';

defineProps({
  errors : Object
})

let form  = reactive({
        name: '',
        email: '',
        password: '',
});

// save method callback call
let save = () => {
    Inertia.post(route('create.user'), form);
};


</script>
