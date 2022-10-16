<template>
    <h1 class="text-lg mb-4">Post</h1>
    <div class="mb-4">
        <Link :href="route('posts.index')" class="hover:bg-white hover:text-black border border-sky-500 block p-2 w-32 bg-gray-500 rounded-full text-center text-white"
        >Back</Link>
    </div>
    <div v-if="post">
        <div class="mt-8 border-t border-gray-300">
            <div>id:{{post.id}}</div>
            <div>title:{{post.title}}</div>
            <div>content:{{post.content}}</div>
            <div class="text-lg text-right">{{post.data}}</div>
        </div>

    </div>
</template>

<script>
import {Link}  from "@inertiajs/inertia-vue3";
import MainLayot from "@/Layouts/MainLayot.vue";

export default {
    name: "index",
    layout: MainLayot,
    props: [
        "post"
    ],
    components: {
        Link
    }
}
</script>

<style scoped>

</style>
