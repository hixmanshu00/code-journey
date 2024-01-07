<template>
    <div class="container mb-3">
        <form action="">
            <div class="mb-3">
                <label for="" class="form-label">Page Title</label>
                <!-- binding value of input w pageTitle and then updating the value using input event handler -->
                <!-- <input type="text" class="form-control" :value="pageTitle" @input="(e) => pageTitle = e.target.value"> -->

                <!-- using v-model to two-way bind the input value -->
                <input type="text" class="form-control" v-model="pageTitle">

            </div>
            <div class="mb-3">
                <label for="" class="form-label">
                    Content
                </label>
                <textarea name="" id="" cols="30" rows="10" class="form-control" v-model="content"></textarea>
            </div>
            <div class="mb-3">
                <button class="btn btn-primary" @click.prevent="pageCreated({pageTitle,content})">Create Page</button>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        props: ['pageCreated'],
        data() {
            return {
                pageTitle: '',
                content: ''
            }
        }
    }
</script>