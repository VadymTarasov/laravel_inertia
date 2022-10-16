<template>
    <h1 class="text-lg mb-4">Posts</h1>
    <div>
        <Link :href="route('posts.create')"
              class="hover:bg-white hover:text-black border border-sky-500 block p-2 w-32 bg-sky-500 rounded-full text-center text-white">
            Add Post
        </Link>
    </div>
    <div v-if="posts">
        <div v-for="post in posts" class="mt-8 border-t border-gray-300">
            <div>id:{{ post.id }}</div>
            <div>title:{{ post.title }}</div>
            <div>content:{{ post.content }}</div>
            <div class="text-lg text-right">{{ post.data }}</div>
            <div class="text-lg text-right">
                <Link class="text-green-600" :href="route('posts.show',post.id)">Show</Link>
            </div>
            <div class="text-lg text-right">
                <Link class="text-sky-500" :href="route('posts.edit',post.id)">Edit</Link>
            </div>
            <div class="text-lg text-right">
                <p @click="deletePost(post.id)" class="cursor-pointer text-red-500">Delete</p>
            </div>
        </div>
    </div>

</template>

<script>
import {Link} from "@inertiajs/inertia-vue3";
import MainLayot from "@/Layouts/MainLayot.vue";

export default {
    name: "index",
    layout: MainLayot,
    props: [
        "posts"
    ],
    components: {
        Link
    },
    methods: {
        deletePost(id) {
            this.$inertia.delete(`/posts/${id}`)
        }
    }
}
</script>

<style scoped>

</style>
