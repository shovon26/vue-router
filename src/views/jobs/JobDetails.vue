<template>
    <div v-if="job">
        <h1>Job information page</h1>
        <p>Job Title: {{ job.title }}</p>
        <p>Job Details: {{ job.details }}</p>
        <p>The job id :: {{ id }}</p>
        <p>{{ print }}</p>
    </div>
    <div v-else>
        <p>Details is loading...</p>
    </div>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return {
            job: null
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs/' + this.id)
            .then(res => res.json())
            .then(data => this.job = data)
            .catch(err => console.log(err.message))
    },
    computed: {
        print(){
            console.log('details is shown')
        }
    }
}
</script>

<style>
    
</style>