<template>
    <nav :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Navbar</a>

            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li v-for="(page, index) in pages" class="nav-item" :key="index" :class="{ active: activePage == index }">
                    <a @click.prevent="navLinkClick(index)" class="nav-link" aria-current="page"
                        :href="page.link.url">{{ page.link.text }}</a>
                </li>
            </ul>

            <button class="btn mx-4" :class="[`btn-${theme}`, 'bg-gradient']" @click.prevent="changeTheme()">
                Light / Dark
            </button>
            <form class="d-flex" role="search">
                <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" />
                <button class="btn btn-outline-success" type="submit">Search</button>
            </form>
        </div>
    </nav>
</template>

<script>
export default {
    props: ['pages', 'activePage', 'navLinkClick'],
    data() {
        return {
            theme: 'dark'
        }
    },

    methods: {
        changeTheme() {
            let theme = "light";

            if (this.theme == "light") {
                theme = "dark";
            }

            this.theme = theme;
        },
    },
}
</script>