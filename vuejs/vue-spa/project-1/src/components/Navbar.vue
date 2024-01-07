<template>
    <nav :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Navbar</a>

            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li v-for="(page, index) in pages" class="nav-item" :key="index" :class="{ active: activePage == index }">
                    <!-- using separate component for nav link -->
                    <navbar-link :page="page" :isActive="activePage === index"
                        @click.prevent="navLinkClick(index)"></navbar-link>
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
import NavbarLink from './NavbarLink.vue';
export default {
    components: { NavbarLink },
    created() {
        this.getThemeSetting();
    },
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
            this.storeThemeSetting();
        },

        // method to store theme value to the localstorage
        storeThemeSetting() {
            localStorage.setItem('theme', this.theme);
        },

        // method to get the value from the localstorage
        getThemeSetting() {
            let theme = localStorage.getItem('theme')
            if (theme) {
                this.theme = theme
            }
        }
    },
}
</script>

