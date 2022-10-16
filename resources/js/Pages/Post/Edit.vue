<template>
    <h1 class="text-lg mb-4">Edit</h1>
    <div class="mb-4">
        <Link :href="route('posts.index')"
              class="hover:bg-white hover:text-black border border-sky-500 block p-2 w-32 bg-gray-500 rounded-full text-center text-white">
            Back
        </Link>
    </div>
    <form @submit.prevent="update">
        <div class="mb-4">
            <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="title">
        </div>
        <div>
            <textarea v-model="content" class="w-full rounded-full border-gray-300" placeholder="content"></textarea>
        </div>
        <div class="w-96 mx-auto pt-2">
            <button
                class="hover:bg-white hover:text-black border border-sky-500 block p-2 w-32 bg-sky-500 rounded-full text-center text-white"
                type="submit"
            >Update
            </button>
        </div>
    </form>

</template>

<script>
import {Link} from "@inertiajs/inertia-vue3";
import MainLayot from "@/Layouts/MainLayot.vue";

export default {
    name: "index",
    layout: MainLayot,
    components: {
        Link
    },
    props: [
        'post'
    ],
    data() {
        return {
            id: this.post.id,
            title: this.post.title,
            content: this.post.content,
        }
    },
    methods: {
        update() {
            this.$inertia.patch(`/posts/${this.id}`, {title: this.title, content: this.content})
        }
    }
}
</script>

<style scoped>

</style>
