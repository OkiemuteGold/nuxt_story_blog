<template>
    <section id="posts">
        <div v-for="post in posts" :key="post.id">
            <PostPreview
                :id="post.id"
                :thumbnailImage="post.thumbnailUrl"
                :title="post.title"
                :previewText="post.previewText"
            />
        </div>
    </section>
</template>

<script>
import PostPreview from "~/components/Blog/PostPreview.vue";
export default {
    components: { PostPreview },

    data() {
        return {
            posts: [
                {
                    id: "a-new-beginning",
                    thumbnailUrl: "../images/food1.jpg",
                    title: "A New Beginning",
                    previewText: "First awesome post here",
                },
                {
                    id: "a-second-beginning",
                    thumbnailUrl: "../images/food2.jpg",
                    title: "A Second Beginning",
                    previewText: "Second awesome post here",
                },
                {
                    id: "a-third-beginning",
                    thumbnailUrl: "../images/food3.jpg",
                    title: "A third Beginning",
                    previewText: "Third awesome post here",
                },
            ],
        };
    },
};
</script>

<style scoped>
#posts {
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
    padding: 1rem;
}
</style>
