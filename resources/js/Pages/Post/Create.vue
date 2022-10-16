<template>
    <h1 class="text-lg mb-4">Create</h1>
    <div class="mb-4">
        <Link :href="route('posts.index')" class="hover:bg-white hover:text-black border border-sky-500 block p-2 w-32 bg-gray-500 rounded-full text-center text-white">Back</Link>
    </div>
    <form @submit.prevent="store">
        <div class="mb-4">
            <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="title">
            <div v-if="errors.title" class="text-red-600 text-sm">{{errors.title}}</div>
        </div>
        <div>
            <textarea v-model="content" class="w-full rounded-full border-gray-300" placeholder="content"></textarea>
            <div v-if="errors.content" class="text-red-600 text-sm">{{errors.content}}</div>
        </div>
        <div class="w-96 mx-auto pt-2">
            <button class="hover:bg-white hover:text-black border border-sky-500 block p-2 w-32 bg-sky-500 rounded-full text-center text-white" type="submit">Store</button>
        </div>
    </form>

</template>

<script>
import {Link}  from "@inertiajs/inertia-vue3";
import MainLayot from "@/Layouts/MainLayot.vue";

export default {
    name: "index",
    layout: MainLayot,
    components: {
        Link
    },
    props: [
        'errors'
    ],
    data(){
        return {
       title: '',
       content: '',
        }
    },
    methods: {
        store(){
            this.$inertia.post('/posts', {title: this.title, content: this.content})
        }
    }
}
</script>

<style scoped>

</style>
