<template>
    <section id="posts">
        <div v-for="post in posts" :key="post.id">
            <PostPreview
                :id="post.id"
                :dateCreated="post.dateCreated"
                :thumbnailUrl="post.thumbnailUrl"
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

    asyncData(context) {
        return context.app.$storyapi
            .get("cdn/stories", {
                version: "draft",
                starts_with: "blog/",
            })
            .then((res) => {
                // console.log(res);

                return {
                    posts: res.data.stories.map((post) => {
                        const date = new Date(post.created_at);
                        let month = date.getMonth();
                        let year = date.getFullYear();
                        let day = date.getDate();

                        post.created_at = `${day} - ${month} - ${year}`;

                        return {
                            id: post.slug,
                            dateCreated: post.created_at,
                            title: post.content.title,
                            previewText: post.content.summary,
                            thumbnailUrl: post.content.thumbnail,
                        };
                    }),
                };
            });
    },

    // async asyncData(context) {
    //     const res = await context.app.$storyapi.get("cdn/stories", {
    //         version: "draft",
    //         starts_with: "blog/",
    //     });

    //     // Let's convert content.date from a String to a Date
    //     const posts = res.data.stories.map((story) => {
    //         const date = new Date(story.created_at);
    //         let month = date.getMonth();
    //         let year = date.getFullYear();
    //         let day = date.getDate();

    //         story.created_at = `${day} - ${month} - ${year}`;

    //         return {
    //             id: story.slug,
    //             dateCreated: story.created_at,
    //             title: story.content.title,
    //             previewText: story.content.summary,
    //             thumbnailUrl: story.content.thumbnail,
    //         };
    //     });

    //     return { posts };
    // },

    // data() {
    //     return {
    //         posts: [
    //             {
    //                 id: "a-new-beginning",
    //                 thumbnailUrl: "../images/food1.jpg",
    //                 title: "A New Beginning",
    //                 previewText: "First awesome post here",
    //             },
    //             {
    //                 id: "a-second-beginning",
    //                 thumbnailUrl: "../images/food2.jpg",
    //                 title: "A Second Beginning",
    //                 previewText: "Second awesome post here",
    //             },
    //             {
    //                 id: "a-third-beginning",
    //                 thumbnailUrl: "../images/food3.jpg",
    //                 title: "A third Beginning",
    //                 previewText: "Third awesome post here",
    //             },
    //         ],
    //     };
    // },
};
</script>

<style scoped>
#posts {
    display: flex;
    flex-flow: row wrap;
    -ms-flex-flow: row wrap;
    justify-content: center;
    padding: 1rem;
}
</style>
