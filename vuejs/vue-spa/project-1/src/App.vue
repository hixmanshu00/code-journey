<template>
    <navbar :pages="pages" :active-page="activePage" :nav-link-click="(index) => activePage = index"></navbar>
    <!-- if data is fetched and assigned to pages only then page prop will be passed to page-viewer -->
    <page-viewer v-if="pages.length > 0" :page="pages[activePage]"></page-viewer>
</template>

<script>
import PageViewer from './components/PageViewer.vue';
import Navbar from './components/Navbar.vue';
export default {
    components: {
        Navbar,
        PageViewer
    },
    // using lifecycle hook to call getPages() method
    created() {
        this.getPages();
    },
    data() {
        return {
            activePage: 0,
            pages: []
        };
    },
    methods: {
        // method to fetch data 
        async getPages() {
            let res = await fetch('pages.json');
            let data = await res.json();
            this.pages = data;
        }
    }
}
</script>