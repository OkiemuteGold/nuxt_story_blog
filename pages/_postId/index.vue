<template>
    <div id="post">
        <div
            class="post_thumbnail"
            :style="{ backgroundImage: `url(${imageUrl})` }"
        ></div>
        <div class="post_content">
            <div class="head">
                <h1>{{ title }}</h1>

                <div class="date_created">
                    <time :datetime="dateCreated"> {{ dateCreated }} </time>
                </div>
            </div>

            <hr />

            <p>{{ content }}</p>
        </div>
    </div>
</template>

<script>
export default {
    asyncData(context) {
        return context.app.$storyapi
            .get(`cdn/stories/blog/${context.params.postId}`, {
                version: "draft",
            })
            .then((res) => {
                console.log(res);

                let createdAt = res.data.story.created_at;
                const date = new Date(createdAt);
                let month = date.getMonth();
                let year = date.getFullYear();
                let day = date.getDate();

                res.data.story.created_at = `${day} - ${month} - ${year}`;

                return {
                    dateCreated: res.data.story.created_at,
                    imageUrl: res.data.story.content.thumbnail,
                    title: res.data.story.content.title,
                    content: res.data.story.content.content,
                };
            });
    },
};
</script>

<style scoped>
.post_thumbnail {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    width: 100%;
    height: 300px;
}

.post_content {
    max-width: 600px;
    margin: auto;
    padding: 15px;
}

.post_content .head {
    text-align: center;
    margin-top: 10px;
    margin-bottom: 20px;
}

.post_content h1 {
    font-size: 1.5rem;
}

.post_content .date_created {
    font-size: 0.825rem;
    font-style: italic;
}

.post_content p {
    white-space: pre-line;
}
</style>