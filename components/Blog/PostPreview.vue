<template>
    <nuxt-link :to="id">
        <article class="post_preview">
            <div class="post_preview_thumbnail_container">
                <div
                    class="post_preview_thumbnail"
                    :style="{ backgroundImage: `url(${thumbnailUrl})` }"
                ></div>

                <div class="date_created">
                    <time :datetime="dateCreated">{{ dateCreated }}</time>
                </div>
            </div>

            <div class="post_preview_content">
                <h2>{{ title }}</h2>
                <p>{{ previewText }}</p>
            </div>
        </article>
    </nuxt-link>
</template>

<script>
export default {
    props: {
        id: {
            type: String,
            required: true,
        },
        dateCreated: {
            type: String,
            required: true,
        },
        thumbnailUrl: {
            type: String,
            required: true,
        },
        title: {
            type: String,
            required: true,
        },
        previewText: {
            type: String,
            required: true,
        },
    },
};
</script>

<style scoped>
a {
    text-decoration: none;
    color: #121212;
}

.post_preview {
    border-radius: 4px;
    box-shadow: 1px 1px 5px 1px rgba(0, 0, 0, 0.45);
    min-width: 16.25rem;
    height: 20rem;
    margin: 1rem 0.875rem;
}

.post_preview_thumbnail_container {
    position: relative;
    top: 2px;
    width: 98.5%;
    margin: auto;
    border-radius: 4px 4px 0 0;
    overflow: hidden;
}

.date_created {
    position: absolute;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.5);
    box-shadow: -1px -1px 3px rgba(255, 255, 255, 0.15);
    color: #fff;
    padding: 1px 6px 0 8px;
    border-radius: 4px 0 0 0;
    font-size: 0.625rem;
}

.post_preview_thumbnail {
    background-size: cover;
    background-position: center;
    filter: contrast(98%);
    -webkit-filter: contrast(98%);
    width: 100%;
    height: 10rem;
    transition: 0.4s ease-in-out;
    -o-transition: 0.4s ease-in-out;
    -moz-transition: 0.4s ease-in-out;
    -webkit-transition: 0.4s ease-in-out;
}

.post_preview:hover .post_preview_thumbnail {
    transform: scale(1.075);
    -o-transform: scale(1.075);
    -moz-transform: scale(1.075);
    -webkit-transform: scale(1.075);
}

.post_preview_content {
    text-align: center;
    padding: 1rem 0.75rem;
}

h2 {
    font-size: 1.25rem;
}

@media screen and (min-width: 1024px) {
    .post_preview {
        min-width: 18rem;
    }
}
</style>