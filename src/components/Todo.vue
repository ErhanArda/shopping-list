<template>
    <div>
        <div v-if="loading">
            Loading...
        </div>
        <ul v-else>
            <li v-for="(todo,id) in todos" :key="id">
                {{todo.title}}
            </li>
        </ul> 
        <div v-if="loading === 'error'">Loading...</div>
    </div>  
</template>
<script>
export default {

    data: function () {
            return {
                loading: true,
                todos: []
            }
        },
    mounted() {
            fetch('https://jsonplaceholder.typicode.com/todos')
                .then(response => response.json())
                .then(json => {
                    this.todos = json;
                    this.loading = false;
                })
                // .catch(error => this.loading = 'error');
        },
        
        
}
</script>