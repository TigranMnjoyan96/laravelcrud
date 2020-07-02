<template>
    <div>
        <div class="col s6">
            <h2>Create Task</h2>
        </div>
        <form @submit.prevent="formSubmit" class="pt-3">

            <div class="input-field col s6">
                <input id="title" type="text" class="validate" v-model="tasks.title">
                <label for="title">Title</label>
            </div>
            <div class="input-field col s6">
                <input id="description" type="text" class="validate" v-model="tasks.description">
                <label for="description">Description</label>
            </div>

            <div class="col s6">
                <button class="btn waves-effect waves-light mt-3" type="submit">Submit
                    <i class="material-icons right">create</i>
                </button>
            </div>

        </form>
    </div>
</template>

<script>
    import {AxiosInstance as axios} from "axios";

    export default {
        name: "Create",
        data() {
            return {
                tasks: {
                    title: '',
                    description: ''
                },
                allTasks: []
            }
        },
        methods: {
            getTasks() {
                axios.get('/api/tasks')
                    .then(res => {
                        this.allTasks = res
                    })
                    .catch(err => {

                    })
            },
            formSubmit() {
                axios.post('/api/tasks/', {
                    title: this.tasks.title,
                    description: this.tasks.description
                })
                    .then(res => {

                    })
            }
        },

        mounted() {
            this.getTasks()
        }
    }
</script>

<style scoped>

</style>
