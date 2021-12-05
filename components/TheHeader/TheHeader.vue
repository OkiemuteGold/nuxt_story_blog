<template>
    <header class="main_header">
        <nav class="main_nav">
            <ul class="nav_links">
                <nuxt-link to="/" tag="li" class="nav_link">
                    <a>All Posts</a>
                </nuxt-link>
                <nuxt-link to="/about" tag="li" class="nav_link">
                    <a>About</a>
                </nuxt-link>
            </ul>
        </nav>
    </header>
</template>

<script>
export default {};
</script>

<style scoped>
.main_header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 4.5rem;
    background: #022d30;
}

.main_nav {
    height: 100%;
}

.nav_links {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    list-style: none;
}

.nav_link {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 1rem;
    padding: 0.25rem;
}

.nav_link a {
    display: block;
    text-decoration: none;
    color: #fff;
}
</style>