<template>
    <section id="about_page">
        <h1>{{ title }}</h1>
        <p>{{ content }}</p>
    </section>
</template>
<script>
export default {
    asyncData(context) {
        return context.app.$storyapi
            .get("cdn/stories/about", {
                version: "draft",
            })
            .then((res) => {
                console.log(res);
                return {
                    title: res.data.story.content.title,
                    content: res.data.story.content.content,
                };
            });
    },
};
</script>

<style scoped>
#about_page {
    max-width: 600px;
    margin: auto;
    padding-top: 1rem;
    text-align: center;
}

#about_page h1 {
    margin-bottom: 15px;
}

#about_page p {
    white-space: pre-line;
}
</style>